---
published: false
---
The hardest thing about building internet applications with microservices is the lack of transactions. While the production issues are nothing to scoff at either, they at least have solutions, either technical or cultural. However, while distributed transactions are possible in theory, in practice they impose too hefty of a performance penalty, and require the kind of deep integration and coordination between actors you aren't likely to encounterl.

So before breaking up that monolith, or starting a new microservices based project, one needs to take extra care around which operations need transactions. If you get this wrong, you'll end up at best with a bad design where you place some non-related data access in a "coordinator" services. At worst you'll have subtle errors in your system, which only manifest themselves when things go wrong.

However, many designs don't need strong consistency and can get by pretty well with eventual consistency.

As an example, a fairly standard microservice to have is one which deals with users and strictly identity related issues, such as user properties, friends etc. and the various auth flows. Oher services make use of this one, and have data associated with users, though stored in their own stores.

A complication arises when a user removes their account. N