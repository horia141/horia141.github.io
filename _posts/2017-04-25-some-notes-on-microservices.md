---
published: false
---
The hardest thing about building internet applications with microservices is the lack of transactions. While the production issues are nothing to scoff at either, they at least have solutions, either technical or cultural. However, while distributed transactions are possible in theory, in practice they impose too hefty of a performance penalty, and require the kind of deep integration and coordination between actors you aren't likely to encounter.

So before breaking up that monolith, or starting a new microservices based project, one needs to take extra care around which operations need transactions. If you get this wrong, you'll end up at best with a bad design where you place some non-related data access in a "coordinator" services. At worst you'll have subtle errors in your system, which only manifest themselves when things go wrong.

However, many designs don't need strong consistency and can get by pretty well with eventual consistency.

As an example, a fairly standard microservice to have is one which deals with users and identity related issues, such as user properties, friends etc. and the various auth flows. Oher services make use of this one, and have data associated with users, though stored in their own stores.

One complication arises when a user removes their account. Naturally we want to inform every service and have them do their natural end-of-life scenarios for that user. Things like marking associated data as removed or sending a farewell email or removing externally stored pictures.

A natural event handler for the "Delete Account" button would first call the users microservice and remove the account, and then cycle through each dependent microserevice and do the same. This won't be transactional, and a failure in the middle of the process will leave the system in an inconsistent state. More or less every approach which does more than one transactional write, be it through multiple calls to microservices, a call to a microservice and an enqueing in a task queue, or even multiple writes to a NoSQL database with just row-level transaction support will result in this same problem.

An improvement would be to just send a message to an at-least once queue, such as [SQS](http://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/standard-queues.html) or [Kafka](https://kafka.apache.org/), and have every microservice listen for the message and react appropriately.

A big downside of this approach is that is requires a commitment to the architecture from the get-go. When gradually evolving a current system it might not make sense to introduce a big dependency like a distributed queue for small use cases, even though in the long term the benefits might be worth it.

A decent solution is to do the user service account deletion as a result of the "Delete Account" hanlder. A small bit of metadata should be associated with the account as well, describing which services have taken note of this removal. It would be initially empty. Something like a JSON list of service names would suffice. Each service would periodically poll the users service for all users which are removed, but for which the particular service hasn't done anything yet. With this info in hand, the service would do it's own thing, such as marking data as removed or sending farewell emails, and then inform the users service that it has done so.

Failure can occur here as well, and the end-of-life processing should be idempotent. As much as possible at least. With something like an farewell message a double delivery could happen. This isn't that different from the guarantees made by an at-least once queue however and I don't see it as a black mark for this approach. That's the price one has to pay in a distributed system.

The other issue is of course, that the system would be in an inconsistent state for a short while, between the initial account removal in the users service and each dependent microservice picking this change up. Most of the time it doesn't matter _that_ much, but extra checks could be placed at query time to ensure that a dependent entity actually has an active user before doing any other sort of processing.
