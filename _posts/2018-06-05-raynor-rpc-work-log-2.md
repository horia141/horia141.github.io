---
layout: post
title: "Raynor RPC Work Log #2"
date: 2018-06-05 08:20:05
categories: post
tags: raynor rpc work-log
comments: true
---
[Last time](https://horia141.com/raynor-rpc-work-log-1.html) I sketched out Raynor RPC. A bit of code got written and put on GitHub but nothing big. In this one I'm going to polish up that thing. The main focus is on getting the annotations right.

The big idea with these annotations is that they're supposed to be a nicer way to describe a service and the mechanics of making an RPC. Consider last episode's example service:

{% highlight ts %}
import { ArrayOf, MarshalWith, MarshalFrom } from 'raynor'
import { nop, Method, Output, Param, Throws } from 'raynor-rpc'
import * as r from 'raynor'

export class Book {
    @MarshalWith(r.IdMarshaller)
    id: number;
    @MarshalWith(r.StringMarshaller)
    title: string;
}

export class TestBookError extends Error {
    constructor() {
        super('Tried to do something with a test book!');
    }
}

export class LibraryService {
    @Method() @Idempotent
    @Output(ArrayOf(MarshalFrom(Book)))
    async getBooks(): Promise<Book[]> {
        return nop();
    }

    @Method()
    @Output(MarshalFrom(Book))
    @Throws(TestBookError)
    async updateBooks(
        @Param(r.IdMarshaller) bookId: number,
        @Param(r.StringMarshaller) newTitle: string): Promise<Book> {
        return nop(bookId, newTitle);
    }
}
{% endhighlight %}

It exists at the source level. At compile time if you will. But we really want it to exist at runtime so it's available as a base for all the other nice things we want to do - generated clients and servers and all the RPC machinery around it. So we would _actually_ want it to be a data structure describing the service. Something like this:

{% highlight ts %}
const libraryServiceDescriptor = {
    "name": "LibraryService",
    "methods": {
        "getBooks": {
            "output": {
                "hasOutput": true
                "marshaller": ArrayOf(MarshalFrom(Book))
            }
            "input": [],
            "idempotent": true
        },
        "updateBook": {
            "output": {
                "hasOutput": true,
                "marshaller": MarshalFrom(Book)
            },
            "input": [{
                "index": 0,
                "marshaller": r.IdMarshaller
            }, {
                "index": 1,
                "marshaller": r.StringMarshaller
            }],
            "idempotent": false
        }
    }
}
{% endhighlight %}

But I don't think it's an understatement to say that this is ugly to both read and write. And it's actually dangerously close to [WSDL and other XML nightmares](https://www.w3.org/TR/2001/NOTE-wsdl-20010315#_soap-e). Luckily TypeScript's decorators allow enough introspection to do the translation from source-level constructs to the description. So we get the best of both worlds - nice syntax and An easy to use data structure in code.

| **Note**: there's other ways of getting this. You could have a separate program which parses the source file and extracts information from it. At least in the JavaScript ecosystem this isn't such an exotic option, cause most teams are going to be using `tsc`, `babel`, `webpack` etc. Ditto, gRPC or Thrift function like this.

So the initial game is to build the annotations and make them extract the proper data. For completeness here is the current set: `Service`, `Method`, `Output`, `NoOutput`, `Throws`, and `Param`.

The descriptors themselves have the following types:
{% highlight ts %}
interface ServiceDescriptor {
    name: string;
    methods: Map<string, MethodDescriptor<any>>;
}

interface MethodDescriptor<T> {
    name: string;
    output?: OutputDescriptor<T>;
    errors?: ErrorDescriptor;
    params: Array<ParamDescriptor<any>>;
}

interface OutputDescriptor<T> {
    hasOutput: boolean;
    marshaller: Marshaller<T>|null;
}

interface ErrorDescriptor {
    errorConstructors: Set<Constructor<Error>>;
}

interface ParamDescriptor<T> {
    index: number;
    marshaller: Marshaller<T>;
    required: boolean;
}
{% endhighlight %}

The actual current sources can be found [here](https://github.com/horia141/raynor-rpc/blob/master/src/core.ts). There's still some issues though, and I haven't managed to capture types for parameters as generic types, just for the output.

| **Note**: one strategy here would be to allow a _single_ parameter to RPC methods. This corresponds to _best_ practices when designing services anyway, cause there's a lot of issues around versioning when you allow multiple parameters and adding and removing them. A second strategy would be to allow _at most_ a _high_ number of them, like 8 and go with that.

The big idea is that after we've run all this decorator code at module load time, the annotated class has a `__service` field which contains the data structure from above. Notice that this bit is very much type unsafe. We don't have the mechanisms to say that a class annotated with `@Service` will have the field. So there's a lot more instances of defensive programming down the line etc.

For example, the code for the `Param` decorator looks like:

{% highlight ts %}
function Param<T>(marshallerCtor: MarshallerConstructor<T>) {
    return function(target: any, methodName: string, parameterIndex: number) {
        const service = _ensureServiceDescriptor(target);
        const method = _ensureMethodDescription(service, methodName);

        method.params[parameterIndex] = {
            index: parameterIndex,
            marshaller: new marshallerCtor(),
            required: true
        };
    }
}
{% endhighlight %}

Notice that we _can_ capture the type of the parameter here, but we can't "store" it for later with the current type system. All of them look more or less the same and you can check them out on [GitHub](https://github.com/horia141/raynor-rpc/blob/master/src/annotations.ts).

**Note**: in Raynor, we can't actually ensure that the type `T` from `Param<T>` which the `MarshallerConstructor` uses is the _same_ or compatible to the actual type of the parameter. The following will actually pass compilation:

{% highlight ts %}
updateBook(@RpcParam(r.StringMarshaller) bookId: **string**, ...) {
   ...
}
{% endhighlight %}

That's it for now. In part 3 we'll focus on actually transforming the description so far into a client and server objects. A sneak preview - well do an in-memory and an Express based implementation at the same time. In this sort of situations I find it very useful to target two approaches at the same time, as possibilities for abstraction and defining the right interfaces crop up better. We won't be tied down to the way a particular approach works. We worry a out context or any of the other big features just yet.
