---
published: true
layout: post
date: '2017-09-01 10:32'
---
   

[Passwords evolved - authentication guidance for the modern era (2017)](https://www.troyhunt.com/passwords-evolved-authentication-guidance-for-the-modern-era/) - busts a lot of common “best practices” people use when building auth systems, like requiring special characters of character hints. There's been several articles on this theme in the Friday blast series, and the overarching message has been that of not trying to roll your own,  but rather rely on the already existing ones.

[Spotify’s love/hate relationship with DNS (2017)](http://labs.spotify.com/2017/03/31/spotifys-lovehate-relationship-with-dns/) - a look into how Spotify uses DNS for both internal and external clients. Internally they use DNS for service discovery, but this yields times of about half an hour for change propagation. Which didn't use to be a problem. But since their move to GCP the machine setup time has gone down significantly, while this time has not. However, the most interesting use is for tracks. Each track they have has an entry in DNS, and various track-level metadata is attached to it, such as the machine which stores it etc. This is the first time I've heard of such a usage for DNS, but it makes sense. It is after all, a very distributed key-value store.

[Performance myths: clusters vs non-clustered indexes (2017)](https://sqlperformance.com/2017/03/sql-indexes/performance-myths-clustered-vs-non-clustered) - only siths deal in absolutes. Sometimes a non-clustered indexes can be faster than an clustered one. The canonical example is a count operation which looks at the most compact index rather than the clustered one, which, almost certainly will have more disk pages than any other index. Well worth subscribing to the blog as well.

[Flash and it's history on the web (2017)](http://thehistoryoftheweb.com/the-story-of-flash/) - a short history lesson on Flash. Brushes over many of its shortcomings however.

[How I built a CMS and why you shouldn't (2017)](https://hackernoon.com/how-i-built-a-cms-and-why-you-shouldnt-daff6042413a?source=rss----3a8144eabfe3---4) - every web developer should know something about how CMSes work and how that whole industry works. This is a gentle introduction as well as a reminder that things are quite matured so you don't need to reinvent the wheel. I also learned what a headless CMS is, which is quite a nice idea.

[How not to sort items (2009)](http://www.evanmiller.org/how-not-to-sort-by-average-rating.html) - a perrenial problem in many web applications is sorting items according to some user-supplied score. The problem is best treated as that of estimating the parameter of a Bernoulli distribution and the score by which to sort is the lower part of the confidence interval for that estimate. There's also examples of how _not_ to do it, with real world implementations that annoy people.

[The inner product as a decision rule (2017)](https://jeremykun.com/2017/05/22/the-inner-product-as-a-decision-rule/) - linear models for classification are the workhorses of machine learning. Logistic regression, the perceptron, linear SVMs, Fisher's discriminant etc all are different forms of linear models. More advanced models such as non-linear SVMs or neural networks build upon these and usually employ them as the output generating layer. It's only fitting that one needs a deep understanding of such models. This article deals with the beautiful geometry behind them, and how the inner product gives valuable insights into the position of a input relative to the decision boundary.
