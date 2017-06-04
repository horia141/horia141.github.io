---
published: true
title: Raynor
layout: post
date: 2017-05-15 12:16:05
categories: post
tags: raynor marshalling
comments: false
math: true
---

What needs to be talked about:

 - Intro: what I've built. A link to the library. Short shout-out to technology involved.
 - Smallest interesting example: an point class. Extract from string and call a method on it.
 - Overview of what the library does, in bigger strokes. Speak about the main use case of describing objects from smaller pieces, and the general one of transforming raw objects into objects which have a certain structure. Where is this useful for. Input & output of the system. When calling into other systems. For storage. With some caveats. For UI validation before sending to the server.
 - Tutorial
   - This is a section which is meant as a "Introduction to Raynor" kind of thing. I'll cover the most common use cases.
   - Speak about Marshallers. Perhaps define a very basic marshaller.
   - Speak about the multitude of marshallers already in place for various types of data.
   - Speak about annotated marshallers and how they're used.
   - Speak about the framework of RaiseBuildFilter marshallers. How to extend the current primitive type marshallers. How to extend the object marshallers and some caveats.
   - Other interesting marshallers: optional, oneof, arrayof, mapof etc.
 - Comparison with other systems. When you might use this.
 - Phylosphy of what to validate.
 - DTOs and storage objects.

Clean
---

A little while ago I wrote and open-sourced a small TypeScript/JavaScript data validation and marshalling library called [Raynor](https://github.com/horia141/raynor). Since it proved quite useful to use around the house, I figured I could do a little bit more with it than just dump it on GitHub. This article is a first step in that direction. It is an overview and tutorial of what Raynor is and how it operates. If you find this sort of stuff interesting I hope this will provide enough info for you to be able to try it in our own projects.

A code example is worth `1000` bytes, so here's one before I say anything more:

{% highlight js %}
class User {
    @MarshalWith(StringMarshaller)
    name: string;
    @MarshalWith(ArrayOf(NumberMarshaller))
    scoresByDay: number[];

    totalScore(): number {
        return this.scoresByDay.reduce((a,b) => a + b, 0);
    }
}

const um = new (MarshalFrom(User))();
const u = new.extract(JSON.parse('{"name": "Raynor", "scoresByDay": [10, 20, 30]}'));
console.log(u.totalScore()); // Prints 60
{% endhighlight %}

As you can see, the core idea is transforming a basic JS object into a more complicated one and checking that certain constraints apply. The actual input is usually the result of some sort of deserialization procedure. In this and many other cases, this would be JSON. But form encoding, URL encoding, some custom binary format etc. can all be used. Since there's such a great variety in both formats and implementations it is currently a non-goal for Raynor to deal with this aspect of marshalling.

The rest of this article is split into two parts. The first is the actual tutorial. The second acts as a rationale for building it and a comparison with other similar systems.

Tutorial
---

Raynor deals with one type of object of its own - the _marshaller_. It is the object which does the transformation and checking mentioned in the interface, through the `extract` method. It can act both ways, however. So, in our example `um` can also transform `u` back into a regular JS object, through the `pack` method. All marshallers are derived from the `Marshaller<T>` interface, which is quite small, and looks like this:

{% highlight js %}
interface Marshaller<T> {
    extract(raw: any): T;
    pack(cooked: T): any;
}
{% endhighlight %}

The template type `T` represents the class to which the marshaller knows how to transform objects. The `extract` method usually does the heavy lifting. The input is `any`, and it commonly is `null`, a boolean, a number, a string, an array or an object. This fact must be checked however, since if a method expects an array, it should fail gracefully when encountering a number. When a condition is encountered which prevents the `raw` from being transformed, an `ExtractError` should be thrown. Finally, `pack` is the reverse of `extract` functionally-wise. Code-wise, it's more the case that it is a much simpler method than `extract`, as many of the validation steps are not needed.

As an example, let's suppose we've encoded booleans as `'TRUE'` and `'FALSE'` in our application, and we wish to have a marshaller that can transform them into proper booleans. This is quite the contrived example, but it will help highlight most of the issues wof writing a marshaller from scratch. It might look something like this:

{% highlight js %}
class CapitalBooleanMarshaller implements Marshaller<boolean> {
    extract(raw: any): boolean {
        if (typeof raw !== 'string') {
            throw new ExtractError('Expected a string');
        }

        const rawRaw = raw.toUpperCase();

        if (rawRaw == 'TRUE') {
            return true;
        } else if (rawRaw == 'FALSE') {
            return false;
        } else {
            throw new ExtractError('Expected either TRUE or FALSE');
        }
    }

    pack(cooked: boolean): any {
        return cooked ? 'TRUE' : 'FALSE';
    }
}
{% endhighlight %}

Builtin Marshallers
===

Naturally, Raynor comes with a bunch of marshallers for the simple types of JavaScript. Things like numbers, booleans, strings, nulls, `Date`s etc. are handled from the start, so you can start building off them. There are also marshallers for very common objects based on these types. For example, `IntegerMarshaller` extends the `NumberMarshaller` and checks that the input is an integer. `PositiveIntegerMarshaller` goes a bit further and checks that the integer is positive. `IdMarshaller` is an alias for this one. `WebUriMarshaller` checks that a string input is in URI form and the protocol is either `http` or `https`.

For example:

{% highlight js %}
const uriMarshaller = new WebUriMarshaller();
console.log(uriMarshaller.extract('http://example.com')); // Prints http://example.com
try {
    uriMarshaller.extract('ftp://example.com');
} catch (e) {
    console.log(e.name); // Prints 'ExtractError'
}
{% endhighlight %}

As a sidenote, my plan is to move these marshallers out of Raynor proper and into a second library, which would contain type definitions and marshallers for the common _business_ type objects one works with: IBANs, currency, geo locations, URIs, emails, etc.

We'll go into more details about how these are implemented later in the article. But a very common way to build a marshaller is to start with an already existing marshaller, which expresses a certain constraint on the input, and add another constraint to it. For example, if your app's domain is `my-app.com` and you want to check that a particular resource you use has a URI from `my-app.com`, you could start with the `SecureWebUriMarshaller` and extend it like so:

{% highlight js %}
class MyAppUriMarshaller extends SecureWebUriMarshaller {
    filter(uri: string): string {
        if (!uri.startsWith('https://my-app.com/')) {
            throw new ExtractError('Expected my-app URI');
        }

        return uri;
    }
}
{% endhighlight %}

You can even extend `MyAppUriMarshaller` once more, to perhaps only allow images, like so:

{% highlight js %}
class MyAppImageUriMarshaller extends MyAppUriMarshaller {
    filter(uri: string): string {
        if (!uri.endsWith('.jpg')) {
            throw new ExtractError('Expected an image URI');
        }

        return uri;
    }
}
{% endhighlight %}

The order in which the `filter` methods are applied is from the base class up to the derived class, or from more general to more specific. So, for example, you can safely assume that the `uri` which makes it to `MyAppImageUriMarshaller` starts with `https://my-app.com/`.

Building Marshallers For Classes
===

A great deal of use cases are covered by these marshallers and their extensions. However, as the inputs turn from simple types to objects, arrays or complex aggregates of them, it becomes tedious and even downright hard to write mardhallers for them. Luckily Raynor comed with a rich set of tools for dealing with these cases, in the form of a set of annotations for class definitions and the supporting infrastructure needed to turn these into marshallers automatically. The marshallers thus built implement the very common pattern of having a complex object be recursively broke down into smaller and simpler objects, which are handled by other types of marshallers.

The initial example in the article used these annotations. We'll focus now on a different and bigger example now in order to dive deeper into the functionality put forth by Raynor.

A classic thing to model is a mathematical point. For starters it might look like this:

{% highlight js %}
class Point {
    @MarshalWith(NumberMarshaller)
    x: number;
    @MarhsalWith(NumberMarshaller)
    y: number;

    constructor(x: number, y: number) {
        this.x = x;
	this.y = y;
    }

    getNorm(): number {
        return Math.sqrt(this.x * this.x + this.y * this.y);
    }
}
{% endhighlight %}

The class has two public properties `x` and `y`, a constructor of two arguments, and an instance function `getNorm`, which returns the mathematical norm $\sqrt{xˆ2 + yˆ2}$. The strinking point is the `MarshalWith` annotation applied to the public properties. A you might have guessed, this informs Raynor of which marshaller to use when trying to construct a `Point`. Any sort of marshaller can be specified, but the actual argument must be a constructor function / class.

In order to create a marshaller, the `MarshalFrom` function is used, which transforms an annotated class into a marshaller class. For example:

{% highlight js %}
const pm = new (MarshalFrom(Point))();
const p = pm.extract(JSON.parse('{"x": 10, y: "20"}')
console.log(pm);
// Prints Point { x: 10, y: 20}
console.log(pm.getNorm());
// Prints 22.36
{% endhighlight %}

Notice the way the function is used with regards to `new`. What it returns is actually a constructor function / class, so you need to obtain an instance before any work can be done. The reason we do this instead of returning an instance directly is for compatibility with the `MarshalWith` annotation. It is very easy to compose marshallers in the same way we compose types. For example, a hypothetical rectangle would look like this:

{% highlight js %}
class Rectangle {
    @MarshalWith(MarshalFrom(Point))
    topLeft: Point;
    @MarshalWith(NumberMarshaller)
    width: number;
    @MarhhalWith(NumberMarshaller)
    height: number;
}
{% endhighlight %}

You can probably intuit what the generated marshaller does. But in broad strokes, it first checks to see if its argument is an object. Then, for each annotated field `f` with a attached marshaller `Mf`, it tries to find the value for property `f` inside the input object, and, once found, use `Mf` to extract the value. This is then written to the property `f` of the output object. If any error is encountered, such as the input object not having a required field, or a sub-marshaller failing, the whole process stops and an `ExtractError` is raised.


More From The Annotations Toolkit
===

`MarshalWith` also accepts a second parameter, which is the name of the field in the original object. It is helpful when dealing with objects from external sources which might not follow your project's style. Our point class might look like this:

{% highlight js %}
class Point {
    @MarhsalWith(NumberMarshaller, '__x') // __x gets mapped to x
    x: number;
    @MarshalWith(NumberMarshaller, '__y') // __y gets mapped to y
    y: number;
    // All the other stuff
}
{% endhighlight %}

A very common pattern, especially for APIs which have been in use for longer periods of time and have seen features added and removed, is for objects to have optional fields in an object. Raynor provides the `OptionalOf` function to turn a regular marshaller into one which is optional, in the context of the annotation system. Extending points to three-dimensional space provides an excellent example for this:

{% highlight js %}
class Point {
    @MarshalWith(NumberMarshaller)
    x: number;
    @MarhsalWith(NumberMarshaller)
    y: number;
    @MarshalWith(OptionalOf(NumberMarshaller))
    z: number;
}

const pm = new (MarshalFrom(Point))();
const p1 = pm.extract({x: 10, y: 20});
console.log(p1);
// Prints Point {x: 10, y: 20, z: null}
const p2 = pm.extract({x: 10, y: 20, z: 30};
console.log(p2);
// Prints Point {x: 10, y: 20, z: 30}
{% endhighlight %}

Raynor comes with a bunch of other utility marshallers, such as `ArrayOf`, `MapOf`, `OneOf2`, `OneOf3`, `MarshalEnum` etc. Together they are meant to provide a rich language for describing the structure and constraints for objects. As an more complex example, consider:

{% highlight js %}
class Mesh {
    @MarshalWith(ArrayOf(MarshalFrom(Point)))
    points: Point[];
    // A map of string->string
    @MarshalWith(MapOf(StringMarshaller))
    metadata: MarshalMap<string>;
    @MarshalWith(OneOf2(StringMarshaller, NumberMarshaller))
    id: string|number;
}
{% endhighlight %}

Note that, in the near future, `MapOf` will be upgraded to work with the ES6 [`Map`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map). There will be a similar `SetOf` which will work with [`Set`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set). There were some problems with TypeScript support for these when emitting to ES5, and I need to figure things out a little bit first, but hopefully it won't be long.

As a final point of behaviour, the marshaller produced by `MarshalFrom` ignores extra fields. It doesn't include them in the output object, even though they would still match the type required according to TypeScript, but it also doesn't raise an error when encountering them. This helps in general with data migration and service evolution inside your own application. It also helps when marshalling responses from external APIs, as only the bits of their response which interests you need be modelled, while the rest can be ignored.

Extending Annotation Marshallers
===

So far the tools provided have been good at modeling validation setups where an object is valid if all of its fields are valid. And, again, as with the simple marshallers, this captures a great deal of use cases. Fortunately, to capture more complex situations, there's no need to introduce a third component to Raynor, but rather build on the ones we already have. We need only extend a marshaller obtained via the annotations mechanism, and provide a `filter` function which describes the extra validation we want to do.

Returning to our two-dimensional point example, suppose we want constrain our points to be on the unit circle. We could achieve this via:

{% highlight js %}
class UnitCirclePointMarshaller extends MarshalFrom(Point) {
    filter(p: Point): Point {
        if (p.getNorm() != 1) {
           throw new ExtractError('Expected a point on the unit circle');
        }
        
        return p;
    }
}
{% endhighlight %}

TypeScript doesn't handle the case of extending a class expression quite well when generating a `.d.ts` file unfortunately for consumption by other packages. So if you want to expose `UnitCirclePointMarshaller` from a package, you'll have to compromise and code it like this:

{% highlight js %}
export class UnitCirclePointMarshaller extends Marshaller<Point> {
    private static readonly _basicMarshaller = new (MarshalFrom(Point))();

    extract(raw: any): Point {
        return this.filter(_basicMarshaller.extract(raw));
    }

    pack(p: Point): any {
        return _basicMarshaller.pack(p);
    }

    filter(p: Point): Point {
        if (p.getNorm() != 1) {
           throw new ExtractError('Expected a point on the unit circle');
        }
        
        return p;
    }
}
{% endhighlight %}

Advanced: RaiseBuildFilter Marshallers
===

Almost all marshallers you've seen here are descendent from `RaiseBuildFilterMarshaller<A, B>`. In fact, only some vary basic marshallers, such as the ones for booleans and `null`s, and the ones used in annotations aren't. Among other things, this marshaller contains the logic for filtering via a hierarchy of marshallers with the `filter` function.

`RaiseBuildFilterMarshaller<A, B>` or `RBFM<A, B>` for short, captures a very common pattern when dealing with deserialization. It breaks down `extract` into three phases: raise, build and an optional filter. Conversely, it breaks down `pack` into two phases: unbuild and lower. Lower is the opposite of raise and ubuild the opposite of filter. Extract takes its input and passes it through the raise operation. This result is then sent through build. Finally, all of the defined filters are applied in the order of most general to most specific. Pack naturally does the reverse. It doesn't do any filtering, but straight up passes the input to unbuild, and the result of that to lower.

The first phase, raise, does very basic checks on the input. Just enough to know that the `any` input is in fact a `number` and not an array or a null. The result of it is usually a JavaScript primitive or object. The type parameter `A` is the output of the `raise` method. The second phase, build, transforms this result into something more structured. Here a `number` might be turned into a `Date` or a `string` into an `EmailAddress`. The type parameter `B` is the output of the `build` method. The result of `build` is something structurally sound. The last phase, filter, which consists of a bunch of methods applied in series, usually apply different business type logic checks. For example, that the `Date` is from this year or that an `EmailAddress` has a certain format.

`RBFM<A, B>` itself is an abstract class, and it is meant to be used as the base in hierarchies of marshallers, where the various marshallers implement different phases. For example, a direct descendant of `RBFM` might implement the raise and lower phases by implementing the `raise` and `lower` methods. A descendent of this one would implement the build and unbuild phases by implementing the `build` and `unbuild` methods. At this point, the latter marshaller is usable as is, since there are no abstract methods left to be implemented. But a whole hierarchy of marshallers can be built on top, each of which only specifying a `filter` function and gradually defining different constraints on the inputs.

As an more concrete example, consider the builtin `PositiveIntegerMarshaller`. It is defined as:

{% highlight js %}
export class PositiveIntegerMarshaller extends IntegerMarshaller {
    filter(b: number): number {
	if (b <= 0) {
	    throw new ExtractError('Expected a positive integer');
	}

        return b;
    }
}
{% endhighlight %}

It only defines a `filter` function which checks that the input is positive. `IntegerMarshaller`, in turn, is defined as:

{% highlight js %}
export class IntegerMarshaller extends NumberMarshaller {
    filter(b: number): number {
        if (Number.isInteger(b)) {
            throw new ExtractError('Expected an integer');
        }

        return b;
    }
}
{% endhighlight %}

It again defines just a `filter` function which checks that the input is positive, via `Number.isInteger`. `NumberMarshaller`, is where things get more interesting. It looks like:

{% highlight js %}
export class NumberMarshaller extends BaseNumberMarshaller<number> {
    build(a: number): number {
	return a;
    }

    unbuild(b: number): number {
	return b;
    }
}
{% endhighlight %}

So it implements the build phase of the `RBFM<A,B>`, with `B = number`. The phase itself is quite simple, being the identity function in both directions. Finally, `BaseNumberMarshaller<number>` looks like:

{% highlight js %}
export abstract class BaseNumberMarshaller<T> extends RaiseBuildFilterMarshaller<number, T> {
    raise(raw: any): number {
	if (typeof raw !== 'number') {
	    throw new ExtractError('Expected a number');
	}

        // isNaN exists in modern browsers.
	if ((Number as any).isNaN(raw) || raw == Number.POSITIVE_INFINITY || raw == Number.NEGATIVE_INFINITY) {
	    throw new ExtractError('Expected a number');
	}

	return raw;
    }

    lower(a: number): any {
	return a;
    }
}
{% endhighlight %}

It implements the raise phase of the `RBFM<A,B>`, with `A = number`. The phase is more involved, with checks for the input being a number, as well as it not being a strange value.

There are many such hierarchies in the builtins of Raynor. The `DateMarshaller` is a similar one, and it also uses `BaseNumberMarshaller` but with `B = Date` this time, since it wants to transform a numeric timestamp to a `Date` object.

Background, Inspiration etc.
---