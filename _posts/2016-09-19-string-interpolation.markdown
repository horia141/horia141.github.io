---
layout: post
title: "String Interpolation - So Hot Right Now"
date: 2016-09-19 22:03:05
categories: post
tags: computer_science programming_languages
comments: true
math: false
---
One of my theories about modern programming languages is that they are all slowly converging towards two-to-five archetypes. And this happens not only on the level of features, but syntax, libraries and the whole ecosystems built around the languages.

That's a broader idea, and one I'll explore in another post. For now, I'm gonna talk about one particular instance of this phenomenon. The adoption of string interpolation by a large number of application programming languages as the way to produce textual output from program data.

By this I mean the ability to do the following:
{% highlight c# %}
var a = 10, b = 20;
var c = a + b;
System.Console.PrintLn($"a = {a} and b = {b} and c = a + b = {c}");
{% endhighlight %}
And see `a = 10 and b = 20 and c = 30` as an output.

Now this is not a ground-breaking thing, but it is one of those small features which really help a programmer at the lowest abstraction levels - the line of code.

The above example is not far-removed from the classic `printf` format of `"a = %d and b = %d and c = %d"`, but it is already a little bit clearer to grok. The neat thing and the full power of this feature is that one can have arbitrary code in a format expression, as long as it is an expression. Here's a neat Python example:
{% highlight python %}
o.write(f'Expires: {expire_time.timestamp()}')
{% endhighlight %}

For statically typed languages, checks can be done at compile time that everything is OK for the expressions in the string. Furthermore, since the format string can be analyzed by the compiler, one gets better protection than with printf-style strings.

Of the top of my head, here's the major languages with support for this: C#, Dart, JavaScript, Python, Ruby, Perl, PHP, Tcl, all the shells basically. The major application level language without support for this is Java.

It is relatively easy to add to a language, so I expect it to make it into most application building languages in the near to medium future, as, it is mostly a syntactic transformation to common library calls.
