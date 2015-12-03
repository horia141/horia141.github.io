---
layout: post
title: "Median Of 5 Elements With 6 Comparisons"
date: 2015-12-03 00:14:05
categories: post
tags: computer_science algorithms puzzles
comments: false
math: true
---
This is a post about a neat CS puzzle I encountered on the Internet and spent some time trying to figure out. I almost gave up after a quarter hour's work initially. However, since I was curious for the right answer, I tried to find it on the web. The hints I found were very opaque and [rushed][berkely], seeming to come straight out of Zeus' head. So I doubled down on finding my own solution, since I figured a nice blog post might come out of it.

__Problem__ As the title of the article suggests, the puzzle is to find the median [[1]][median-wiki] [[2]][median-nist] of $$5$$ comparable items using at most $$6$$ comparisons. More formally, given a sequence $$A = [a_1, a_2, a_3, a_4, a_5]$$ of distinct comparable items, find an element $$m$$ such that there exist distinct $$a,b,c,d \in A \setminus \{m\}$$ with $$\{a,b\} < m < \{c,d\}$$.

Now, there are well known linear median algorithms [[1]][median-algos1] [[2]][median-algos2] to solve this problem, so $$\Theta(5)$$ sounds reasonable. But the trick is to get it to exactly $$6$$ comparisons.

My approach is to use comparisons selectively in order to build a partial order on the set of elements, with enough information to extract the median, but without going to the hassle of actually sorting the sequence.

We first start by comparing $$a_1$$ and $$a_2$$. We can name the smaller $$a$$ and the larger $$b$$ and we have $$a < b$$. _We've used $$1$$ comparison_.

We then look at $$a_3$$ and compare it with $$b$$. We either get $$a < b < a_3$$ or $$\{a,a_3\} < b$$ out of this. In the latter case we use another comparison to establish order between the smaller two elements. At the end of the stage we have $$3$$ sorted elements. Name the smallest one $$a$$, the middle one $$b$$ and the largest one $$m$$. We have $$a < b < m$$. _We've used at most $$3$$ comparisons_.

Now, compare $$a_4$$ and $$a_5$$. We can name the smaller $$c$$ and the larger $$d$$ and we have $$c < d$$. _We've used $$4$$ comparisons_.

Now, take $$c$$ and compare it to $$m$$. If it's larger we have $$a < b < m < c < d$$, which allows us to simply output $$m$$ as the median. _We've only used at most $$5$$ comparisons_.

On the other hand, if the comparison shows that $$c < m$$, we've established that $$\{a < b, c < d\} < m$$ xor $$\{a < b, c\} < m < d$$. In either case, only $$a,b,c$$ can claim to be the median. And, more precisely, since $$a < b$$ is known, $$a$$ can never be the median, since it only has $$c$$ to be larger than in this set. Hence, we need only perform one last comparison between $$b$$ and $$c$$ and output the larger of the two as the median. In one case we have $$a < b < c$$, while in the other we have $$\{a, c\} < b$$. _We've used at most $$6$$ comparisons_.

This is it. Hopefully the explanation makes some sense. I wrote a small Python program to illustrate the approach in a more algorithmic fashion.

{% highlight python %}
def median5(seq):
    assert len(seq) == 5

    # Find a < b. One comparison.
    if seq[0] < seq[1]:
        a = seq[0]
        b = seq[1]
    else:
        a = seq[1]
        b = seq[0]

    # Find a < b < m. Three comparisons.
    if seq[2] > b:
        # Largest.
        m = seq[2]
    else if seq[2] > a:
       # Between a and b.
        m = b
        b = seq[2]
    else:
        # Smaller than a.
        m = b
        b = a
        a = seq[2]

    # Find c < d. Four comparisons.
    if seq[3] < seq[4]:
        c = seq[3]
        d = seq[4]
    else:
        c = seq[4]
        d = seq[5]

    # Find median. Six comparisons.
    if c > m:
        # The a < b < m < c < d case.
        median = m
    else:
        # The {a < b, c < d} < m xor {a < b, c} < m < d case.
        if b < c:
	    # The a < b < c case.
  	    median = c
        else:
            # The {a, c} < b case.
	    median = b   

    return median
{% endhighlight %}

The resulting program is a little bit longer than I expected, but it is basically an unrolled loop.

[median-wiki]: https://en.wikipedia.org/wiki/Median
[median-nist]: https://xlinux.nist.gov/dads//HTML/median.html
[median-algos1]: http://dhost.info/zabrodskyvlada/3alg.html
[median-algos2]: http://www.i-programmer.info/babbages-bag/505-quick-median.html
[berkely]: https://www.ocf.berkeley.edu/~wwu/cgi-bin/yabb/YaBB.cgi?board=riddles_cs;action=display;num=1061827085