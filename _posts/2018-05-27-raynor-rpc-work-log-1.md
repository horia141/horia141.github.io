---
layout: post
title: "Raynor RPC Work Log #1"
date: 2018-05-27 15:20:05
categories: post
tags: raynor rpc work-log
comments: true
---
I'm going to try something different with this blog post and make it a sort of work log for a small project I'm trying to build.

You might remember [Raynor](https://horia141.com/raynor.html) - my small TypeScript marshalling library from some time ago. It allows one to automate a lot of the boilerplate around serialization/deserialization and data validation with the help of annotations. I've used it in a bunch of small projects and I've been really happy with how it works. There's a bunch of stuff to polish and improve for a future major version, but nothing brutally bad.

This got me thinking that I should use it for other things as well. And a natural thing is as part of an RPC library. It's fairly natural for these types of projects to go hand in hand. You can see it with gRPC or Thrift for example.

So this blog post is a rough design document for something I want to call "Raynor RPC". It's going to be a bit rougher than my usual fare.

First things, first. **So, [what's my motivation](https://5writers.com/2012/09/01/whats-my-motivation/)?** Well it's mostly a learning experience, event though I do hope to battle test it in a project. I do think a JavaScript only approach has its merits though, since it can be finely tuned to the specifics of the language and the few platforms it runs on. To my knowledge, there isn't anything like this yet. Sure, gRPC or Thrift can generate JavaScript for Node, but it's usually a second class citizen behind Java or C++. It also limits the thing, but not so much as you'd think. One could technically use JavaScript from embedded software to big servers in the cloud. I also like that in Raynor you can attach small bits of logic as functions to the entities you're defining, and that'll carry over to Raynor RPC. Other system's IDLs don't allow such things, by definition.

The main things I want to have are:
* Keep the annotation approach of Raynor.
* Use Raynor marshalling for making sure parameters are OK at the client and server side.
* Acknowledge the semantics of RPCs - so use `async/await` and `Promise`s, but provides some of the niceties of regular calls. Allow exceptions thrown on the server to be handled by the client.
* Integrate and make use of TypeScript powerful type's system. There will probably be a lot of _lower-level_ magic happening, but clients shouldn't be exposed to it.
* Have a single place where a service is defined. Client and server infrastructure should be derived by the library automatically.
* Should be _transport agnostic_. But I'll be starting with HTTP as the assumed _transport_, JSON for data exchange and building on top of [Express](https://expressjs.com/) for server-side support. But those shouldn't be assumptions, and adding TCP, Koa or binary data to the mix shouldn't dramatically change things.
* Should allow for request metadata to be sent from clients and accessed on the server-side.
* Should allow for server-side middleware. Pure HTTP servers aren't the only ones where placing authentication into middleware makes sense.
Things will get fleshed out more as I develop this thing.

Now, I'd _like_ to get the code to look like the following small example. Suppose we have a library service which allows one to query for the books available and change the titles of a particular book. We can have the `library-sdk` package, which defines the entities and services. It is meant to be used both by clients of the library service, to generate the client objects and work with entities, and by the server itself, to generate server objects.

{% highlight ts %}
// In index.ts
import { ArrayOf, MarshalWith, MarshalFrom } from 'raynor'
import { doRpc, Rpc, RpcOutput, RpcParam } from 'raynor-rpc'
import * as r from 'raynor'

// A pretty standard Raynor annotated class. It is our service's _entity_.
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

// Now, we get to the service definition. At this point, we're only interested
// in its _interface_, and won't/can't specify anything about the
// implementation. This should ideally be an interface, but you can't annotate
// or otherwise work with it because it's a compile-time construct, which won't
// make it to the JavaScript side. Ditto for abstract methods. So we have to use
// a regular class, with a bit of library-provided glue to make things work.
export class LibraryService {
    // The @Rpc annotation marks a method as being a remote procedure call.
    // The doRpc() method is provided as a placeholder so TypeScript won't
    // complain. You can technically provide any body, but it _will_ be
    // ignored in the generated client and server classes. This _must_ be
    // an async function returning a `Promise`. At some point it will be
    // possible to check at runtime for this in the annotation, but not yet.
    @Rpc() @Idempotent
    @RpcOutput(ArrayOf(MarshalFrom(Book)))
    async getBooks(): Promise<Book[]> {
        return doRpc();
    }

    // The possible errors which can be thrown also need to be marked. Java
    // says hello! I'm not married to this idea though, and later designs
    // might drop it, with some small _reduction_ in the information carried
    // along with errors.
    @Rpc()
    @RpcOutput(MarshalFrom(Book))
    @RpcThrows(TestBookError)
    async updateBooks(
        @RpcParam(r.IdMarshaller) bookId: number,
        @RpcParam(r.StringMarshaller) newTitle: string): Promise<Book> {
        return doRpc(bookId, newTitle);
    }

    // It's perfectly fine to have non @Rpc-ed methods here. They will be
    // available in the client and server classes, and no _magic_ will
    // happen to them.
    isTestId(bookId): boolean {
        return bookId < 10000;
    }
}
{% endhighlight %}

In the `library-server` application we actually define the implementation of the `LibraryService` and make it available over the network as a HTTP server. It might looks something like this:

{% highlight ts %}
import * as express from 'express'
import { ExpressHttpServer, Server} from 'raynor-rpc'

import { Book, TestBookError, LibraryService } from 'library-sdk'

// This is just a regular class which extends `LibraryService` and overrides
// it's existing methods. All @Rpc methods need to be overriden! Other than
// that, the class can behave like a regular one. A manual dependency injection
// occurs in this one, for example to pass in a repository object which deals
// with storage interaction.
class LibraryServiceImpl extends LibraryService {
    constructor(private readonly libraryRepository: LibraryRepository) {
    }

    // Nothing special needs to happen here - no annotation or anything. Though
    // you need to respect the signature of `getBooks`. Luckily TypeScript
    // enforces this - there's no function overloading with inheritance.
    async getBooks(): Promise<Book[]> {
        const books = await libraryRepository.getAllBooks();
        return books.filter(b => !this.isTestId(b));
    }

    async updateBooks(bookId: number, newTitle: string): Promise<Book> {
       if (this.isTestId(bookId)) {
           throw new TestBookError();
       }

       const book = await libraryRepository.getBookById(bookId);
       book.title = newTitle;
       await libraryRepository.updateBook(bookId, book);
    }
}

// Now, we setup the server. Notice that we're working with the implementation
// object now.
const repository = new LibraryRepository();
const serviceImpl = new LibraryServiceImpl(repository);

// Not really 100% with what happens next. It'll get fleshed out later though.
// Implementation wise I'd expect to have an `GET /getBooks` endpoint returning
// some JSON, and a `POST /updateBooks` endpoint accepting some JSON and
// returning some JSON as well. But that's an implementation detail.
const server = new Server(serviceImpl);
const httpServer = new ExpressHttpServer(server);

// The rest is a regular express setup. You can define other routes and routers
// as you like.

const app = express.Express();
app.use("/api/library", httpServer.router);

app.listen(80, '0.0.0.0', () => {
    console.log('We\'re in business');
});
{% endhighlight %}

Finally, in the `library-frontend` package, which implements the frontend as a SPA, we want to use the library service. Thinghs would looks like this:

{% highlight ts %}
import { Client, HttpClient } from 'raynor-rpc'

import { Book, LibraryService, TestBookError } from 'library-sdk'

async function markBadBooks(): Promise<Book[]> {
    // First we setup the client. Notice that we're working with the _interface_
    // object.
    const client = new Client(LibraryService);
    const httpClient = new HttpClient(client, 'http://library-server/api/library');

    try {
        const books = await client.getBooks();
        const badBooks = books.filter(b => b.title.contains('Bad'));
        for (const badBook of badBooks) {
            // Done serially here for simplicity
            await client.updateBook(badBook.id, `${badBook.title} - WATCH OUT`);
        }
    } catch (e) {
        if (e instanceof TestBookError) {
            console.log('Tried to work with a test book! Not good');
            return;
        }
        console.log(e);
    }
}
{% endhighlight %}

Ok, so that should be a rough outline of a v1 API for client and server components. It should be pretty familiar to people who've encountered gRPC/Thrift before. And hopefully it should be intuitive enough for everyone else. One important thing to notice is that on the client side there isn't anything to _code_ in order to use this. Everything is done by the library, because all that _can_ be done is usually very repetitive and mechanic. And I'm referring here to things like - argument marshalling, HTTP connection setup, waiting for the response and parsing it and checking that it's valid, handling various errors etc. On the server side there's the same concerns, but you also have to code a bit. But just the actual _important_ parts. Once a method like `updateBooks` executes, you can be sure that `title` exists and is a string, or that `bookId` is a non-negative integer.

Codewise, there's some _sketches_ at [github.com/raynor-rpc](https://github.com/raynor-rpc) - but it's marked with version `'0.0.0'` for a reason. It's basically just enough to check that the annotations based API will work, but nothing more. As I'll build on it I'll post new articles and hopefully I can build a nice series out of this.

---

For the sake of me remembering things, here's some other nice things to have:
* An annotation for idempotent methods. This could impact the server-side APIs that are generated - ie, have a `GET`, rather than a `POST` or `PUT` when using the HTTP infrastructure.
* An annotation to mark void outputs more clearly.
* Support for "fire-and-forget" or one-way methods like in Thrift, for methods with a void output.
* Support for optional parameters.
* Some notion of API versioning and compatibility.
* Support for service proxies for use in [backends for frontends](https://samnewman.io/patterns/architectural/bff/).

And since we're at the dreaming stage, we could also provide, further down the line:
* Call mechanics - timeouts, retries, pipelining, backpressure etc.
* API documentation and debug interaction UI, like Swagger.
* Built in support for monitoring, tracing and logging of API calls.
* Support for streaming responses, especially via the new [async iteration](http://2ality.com/2018/04/async-iter-nodejs.html) in newer versions of JavaScript.
* Support for streaming request data, like the bi-directional streaming in gRPC.
