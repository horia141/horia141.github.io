---
layout: post
title: "Tabletests"
date: 2015-08-31 20:20:05
categories: jekyll update
tags: python tabletest unittest testing
---
This article is an introduction and justification for [tabletest][tabletest] and [tabletest3][tabletest3]. These are small Python and Python3 (respectively) packages I've written, for helping with the writing of so-called "tabletest".

We can all agree that it's nice to have small and concise functions. And if they're side effect free, even better. Such functions are easy to understand, easy to work with and easy to test. The only way such functions would be better would be if we did not need them at all.

Suppose for the sake of argument we have a small function for converting string of binary digts into the integers they represent. We'll call the function `parse_bin`. It operates on strings such as `1010`, on which it would output `10`. Basic stuff. I've coded such a function in Python.

{% highlight python %}
def parse_bin(bin_str):
  """Parse a string of binary digits and produce the integer value represented."""
  result = 0
  pow = 1
  for digit in reversed(bin_str):
    assert digit == '0' or digit == '1'
    digit_dec = 1 if digit == '1' else 0
    result += digit_dec * pow
    pow = pow << 1
  return result
{% endhighlight %}

The function is side effect free. It's also small and relatively concise. I think you'll agree this scores pretty well on the easy to understand and easy to work with scales. How about the easy to test scale? How would unit tests look like for it?

A first approach might look something like the following. A plain `unittest` test case, with one test for each example we wish to verify.

{% highlight python %}
import unittest

class ParseBin(unittest.TestCase):
  def test_parse_bin_empty_string(self):
    self.assertEqual(parse_bin(('', 0))

  def test_parse_bin_zero(self):
    self.assertEqual(parse_bin(('0', 0))

  def test_parse_bin_one(self):
    self.assertEqual(parse_bin(('1', 1)

  def test_parse_bin_leading_zero(self):
    self.assertEqual(parse_bin(('00', 0))

  def test_parse_bin_leading_zero2(self):
    self.assertEqual(parse_bin(('01', 1))

  def test_parse_bin_two(self):
    self.assertEqual(parse_bin('10', 2))

  def test_parse_bin_three(self):
    self.assertEqual(parse_bin('11', 3))
{% endhighlight %}

This thing is very clunky. I'm not inspired to add any more tests than the minimum required. It's hard to grok what's tested and what's not, and a lot of the ceremony and boilerplate of unittesting is repeated between tests. It's not a big deal for this simple case, but one can easily imagine a more complicated setup. There are some good things however. Each example is a separete test. If it fails, the rest of the test suite continues to run. So it's easy to identify errors and we don't get stuck in the "fix one test, run, fix next text" bad habit. Also, as a purely psychological effect, it is nice to see the number of tests for the application increase, as would with the standard test runners.

However, in order to increase the number of tests, we might employ the following pattern, which I'm calling tabletest.

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
    ]

  def test_parse_bin(self):
    for (input, expected) in TEST_CASES:
      self.assertEqual(parse_bin(input), expected)
{% endhighlight %}

Adding test cases has become easy - simply extend `TEST_CASES` with a new `input => expected` pair. However, we are doing the manual work of iterating over test cases ourselfes. Furthermore, the tests are coupled. If one of them fails, the whole suite fails. It becomes hard to perform debugging, unlike the previous case. Finally, the nice psyschological effect of seeing several test cases in the runner is gone. We only have the one test case.

As a solution to all these problems, we can use [tabletest][tabletest]. This is a small extension to the standard `unittest` package, which allows a quick definition of such tests. The translation from the previous example is straightforward. The resulting `TableTestCase` will have one variant of `test_parse_bin` for each example in `TEST_CASE`. We can easily add more test cases now. When an issue occurs, we can spot the failing example fast. Finally, we'll get a proportional number of entries in the test runners.

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
    ('10000', 16),
    ('100001', 33),
    ('0110001', 49)
    ]

  @tabletest.tabletest(TEST_CASES)
  def test_parse_bin(self, test_case):
    (input, expected) = test_case
    self.assertEqual(parse_bin(input), expected)
{% endhighlight %}

There you go! The best of both worlds.

See the next [post][how-tabletest-works] in the series for a deeper dive into how the package actually works.

[tabletest]: https://github.com/horia141/tabletest
[tabletest3]: https://github.com/horia141/tabletest3
[how-tabletest-works]: /jekyll/update/2015/09/08/how-tabletest-works.html