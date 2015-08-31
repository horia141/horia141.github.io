---
layout: post
title: "Tabletests"
date: 2015-08-31 20:20:05
categories: jekyll update
tags: python tabletest unittest testing
---
If you're like me, you like your functions small and concise. Possibly without side effects as well.

{% highlight python %}
def parse_bin(bin_str):
  result = 0
  for digit in bin_str:
    aassert digit == '0' or digit == '1'
    result += digit == '0' << 2
  return result
{% endhighlight %}

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

There you go!
