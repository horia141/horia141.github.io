---
layout: post
title: "Tabletests"
date: 2015-08-31 20:20:05
categories: post
tags: python tabletest unittest testing
comments: true
---
This article is an introduction and justification for [tabletest][tabletest] and [tabletest3][tabletest3]. These are small Python and Python3 (respectively) packages I've written. They are used when writing so-called "tabletests" or data-driven tests.

I'll cause no controversy by saying that functions which are small and concise, are a "good thing". Such functions are easy to work with, easy to understand and easy to test.

For the sake of argument, suppose we have a small function for converting strings of binary digits into the integers they represent. We'll call it `parse_bin`. It operates on strings such as `"1010"` and outputs numbers. Basic stuff really. If we were to code it in Python, it might look something like this:

{% highlight python %}
def parse_bin(bin_str):
  """Parse a string of binary digits and produce the integer value."""
  result = 0
  pow = 1
  for digit in reversed(bin_str):
    assert digit == '0' or digit == '1'
    digit_dec = 1 if digit == '1' else 0
    result += digit_dec * pow
    pow = pow << 1
  return result
{% endhighlight %}

The function scores pretty well on being easy to work with and, hopefully, it's pretty easy to understand as well. However, it is, I claim, quite hard to test.

For example, using Python's standard `unittest` library, the test suite might look something like this:

{% highlight python %}
import unittest

class ParseBin(unittest.TestCase):
  def test_parse_bin_empty_string(self):
    self.assertEqual(parse_bin(''), 0)

  def test_parse_bin_zero(self):
    self.assertEqual(parse_bin('0'), 0)

  def test_parse_bin_one(self):
    self.assertEqual(parse_bin('1'), 1)

  def test_parse_bin_leading_zero(self):
    self.assertEqual(parse_bin('00'), 0)

  def test_parse_bin_leading_zero2(self):
    self.assertEqual(parse_bin('01'), 1)

  def test_parse_bin_two(self):
    self.assertEqual(parse_bin('10'), 2)

  def test_parse_bin_three(self):
    self.assertEqual(parse_bin('11'), 3)
{% endhighlight %}

This looks clunky. It has too much boilerplate and too little action. The worst part is that adding another test is quite involved. We need to define a new function and write a small amount of very repetitive code for it. Hence, we'll want to skip on testing and do the minimum required, rather than write a more comprehensive battery of tests. For example, we haven't tested very large integers and the overflow patterns, or invalid inputs etc. While this example is certainly contrived, one could easily imagine things escalating for more complex functions.

A natural second version factors out the common testing code and makes just a single, data-driven test. It might look something like this:

{% highlight python %}
import unittest

class ParseBin(unittest.TestCase):
  TEST_CASES = [
    ('', 0),
    ('0', 0),
    ('1', 1)
    ('00', 0),
    ('01', 1),
    ('10', 2),
    ('11', 3),
    ('000', 0),
    ('001', 1),
    ('010', 2),
    ('011', 3),
    ('100', 4),
    ('1000000000000000', 2**15),
    ]

  def test_parse_bin(self):
    for (input, expected) in TEST_CASES:
      self.assertEqual(parse_bin(input), expected)
{% endhighlight %}

This approach is an improvement since it makes it easy to add new test cases. In fact, we only need to add an `(input, expected)` pair to add a new case, which is the minimum we could expect. This even opens the door for automatically generated cases, rather than hand coded ones.

The approach comes with its own limitations, however. For example, we've been made responsible for the boilerplate of iterating over each test case. This is a little bit like being responsible for calling the `setUp` and `tearDown` methods ourselves. Sure, they're separated into methods, and reusable, but the situation looks like one which should be handled by the testing framework, rather than by us. Furthermore, testing is coupled. If one case fails, the whole suite fails. For this simple example, it is pretty straightforward to figure out where the failure occurs. For more complicated setups, this might not be the case. The coupling itself is troubling regardless of other concerns, since it is a good principle to have tests be independent. Linked to the last issue, sophisticated test runners might run tests in parallel. Since we've combined all the previous separate tests into a single one, we've lost that capability. The test might become too big and require additional resources or its execution time might become unwieldy. Finally, there is a nice feeling to adding a new test and seeing a new entry in the test runner output for it. We definitely loose this treat by writing things this way.

At this point, one might argue that the cure is worse than the illness. Certainly, there are a lot of drawbacks. We need not resign ourselves to clunky XOR unwieldy tests however. We can have the best of both worlds.

All of this is a long way to introduce the [tabletest][tabletest] library, which is a `unittest` extension which allows one to have data driven tests, but with all the advantages of separate and independent unit tests.

At this point, it would be better to let the code speak for itself. The third and final version of the test suite looks something like this:

{% highlight python %}
import tabletest

class ParseBin(tabletest.TableTestCase):
  TEST_CASES = [
    ('', 0),
    ('0', 0),
    ('1', 1)
    ('00', 0),
    ('01', 1),
    ('10', 2),
    ('11', 3),
    ('000', 0),
    ('001', 1),
    ('010', 2),
    ('011', 3),
    ('100', 4),
    ('101', 5),
    ('110', 6),
    ('111', 7),
    ('1000000000000000', 2**15),
    ('10000', 16),
    ('100001', 33),
    ('0110001', 49),
    ]

  @tabletest.tabletest(TEST_CASES)
  def test_parse_bin(self, test_case):
    (input, expected) = test_case
    self.assertEqual(parse_bin(input), expected)
{% endhighlight %}

The difference between the two versions is that we've replaced the manually iterating version of `test_parse_bin` with a new one, which is annotated with the `tabletest` annotation. Hopefully the way to use it is clear.

Under the hood, the library generates a version of `test_parse_bin` for each test case. Therefore the code that gets executed looks like the first version rather than the second. We still get all the goodness of independent tests and boilerplate-free development, without having to develop it ourselves. Finally, the test runner is going to show one entry for each test case, which will keep us hooked on writing them.

Usage should be straightforward and surprise free. For more info, tune in to the next [post][how-tabletest-works] in the series.

[tabletest]: https://github.com/horia141/tabletest
[tabletest3]: https://github.com/horia141/tabletest3
[how-tabletest-works]: {% post_url 2015-09-08-how-tabletest-works %}