---
layout: post
title: "How Tabletest Works"
date: 2015-09-08 07:10:05
categories: post
tags: python tabletest unittest testing
comments: true
---
In a [previous][tabletests] post I introduced the `tabletest` library. In this post I'm going to dive a little bit into its inner workings. The water is relatively shallow however, since, at less than `80` lines of commented code, the library is not _that_ big to begin with.

I started the project in order to make writing tests for the [SDHash][sdhash] project easier. As such, I had a pretty clear idea of the API I wanted to have. I did not know what tools were available in Python and how I should actually write the thing. In fact, I did not even know if such a thing was doable at all. As we'll see, it was indeed doable (spoiler!), by using Python meta classes, which is one of the more powerful features in the language.

I wanted the API to be really simple - write a list/set/dict/anything iterable of test cases and annotate a "seed" function with the test cases. The library should figure out the rest and do its magic, and generate one test function per test case, as described in the [previous][tabletests] post.

Marking a "seed" function with test cases is done with the `tabletest` annotation. This receives a single argument, which is an iterable object of test cases from which each individual test function is generated. As an implementation detail, the annotation simply adds the test cases as a field to the function object it is applied to. The function is also marked as being processed by `tabletest`..

Have a look at the code:

{% highlight python %}
class tabletest(object):
    def __init__(self, test_cases):
        self._test_cases = iter(test_cases)

    def __call__(self, tester_fn):
        tester_fn._is_tabletest = True
        tester_fn._test_cases = self._test_cases
        return tester_fn
{% endhighlight %}

As you saw in the first [post][tabletests], this is not all that's needed to be done. There is one other small step. The test suite class has to be derived from `TableTestCase` rather than from `TestCase`. The base class of the former is still `TestCase`, and its own behavior is very simple, hence the thing should behave like any other `TestCase` derived class. The only thing that it does is to add `TableTestMetaclass` as the metaclass.

The real magic happens in the meta class, which gets to modify the test suite, much like the annotation gets to modify the function object. The way it works is straightforward. In the `__new__` method we get to inspect the attributes of the object. The goal is to build a new set of attributes, which is identical to the original one, but which has one test function for each test case. We look for those attributes which are both callable/functions and which seem to have been modified by the `tabletest` annotation. For these, we look at all the test cases that are specified, which just means looking at the `_test_cases` field in them, and generate one new test function for each test case. If the annotated function is `test_simple`, then, for three test cases, the functions `test_simple_0`, `test_simple_1` and `test_simple_2` are generated. Each one conforms to the `unittest` conventions, so they are zero-argument methods. All other attributes are left as they were.

There are some fine points to consider. First of, the name of the annotated function must begin with `test` as per the `unittest` convention. Second, there can be more than one annotated function. The library will do the "right thing" and generate several groups of tests. Third of, if a name clash occurs when generating the test functions, an error is raised. Fourth and finally, deriving from `TableTestCase` is not essential, but rather a nice way to package the whole meta class thing. If for some reason, you can't derive from it, you could just as readily specify the meta class yourself. This is why `TableTestMetaclass` is public.

The full code follows:

{% highlight python %}
class TableTestMetaclass(type):
    def __new__(cls, name, bases, attrs):
        new_attrs = {}
        for name, attr in attrs.items():
            if hasattr(attr, '__call__') and hasattr(attr, '_is_tabletest'):
                test_idx = 0
                for test_case in attr._test_cases:
                    test_name = '{0}_{1}'.format(name, test_idx)
                    if test_name in new_attrs:
                        raise Exception('Name "{0}" is already used'.format(test_name))
                    new_attrs[test_name] = \
                        lambda self, attr=attr, test_case=test_case: attr(self, test_case)
                    test_idx += 1
            else:
                new_attrs[name] = attr

        return type.__new__(cls, name, bases, new_attrs)
{% endhighlight %}

Coming in to this project, I did not know if it was doable or not in the form I had envisioned. Even though I've been programming in Python for quite some time, I had managed to avoid meta classes. I only knew I needed something which would change or pre-process the whole class definition before the point of the test harness instantiating the object. It turned out that meta classes were just the tool for the job.

As a final note, the only reason there are two packages, [tabletest][tabletest] for Python 2 and [tabletest3][tabletest3] for Python 3 is because the way to specify the meta class differs in an incompatible way between the two. Such is life.

Anywho, this is it for now.

[sdhash]: https://github.com/horia141/sdhash
[tabletests]: {% post_url 2015-08-31-tabletests %}
[tabletest]: https://github.com/horia141/tabletest
[tabletest3]: https://github.com/horia141/tabletest3