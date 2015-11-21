---
layout: post
title: "Ruby Performance : Case vs. If-elsif"
date: 2011-08-26 19:40
comments: true
categories: [ruby,case,if-elsif,performance,profiling]
---
In this edition of [Ruby Performance](/blog/topics/performance) I take a look at `case` vs. `if-elsif`.

In my testing, links below, it is clear that `case` statements are consistently more expensive than `if-elsif`.  The difference in a single call is insignificant, but that difference adds up over time to possibly matter.

I am certainly not recommending that you use `if-elsif` in every instance.  There are times when the trade-off may be worth the difference in performance.

## Case ##

Case offers less typing, but implicitly compares using the more expensive `===` operator.  Case may also offer more concise code when determining if a value falls within a range of values or a non-contiguous set of multiple values.  Case code also looks prettier in most instances.

## If - Elsif - Else ##

If-elsif-else offers speed of execution and more conspicuous code in some instances.  But the fact remains that it is always faster than `case`.

Here are the timing summaries for strings:

    Timings for [case when using strings]
    Total: 3.587024

    Timings for [if elsif else using strings]
    Total: 2.380505

Here are the summaries for integers

    Timings for [case when using integers]
    Total: 3.495027

    Timings for [if elsif else using integers]
    Total: 2.570731

I also wanted to see the difference between the `===` operator with if-elsif and case which implicitly uses `===`

    Timings for [case when using integers]
    Total: 3.495027

    Timings for [if elsif else using integers with ===]
    Total: 3.561783

So in this case, no pun intended, the `case` statement is <del>faster</del> slower.

Find the tests here: [https://github.com/midwire/ruby-profiles/raw/master/case_vs_if.rb](https://github.com/midwire/ruby-profiles/raw/master/case_vs_if.rb)

Regards,

-- Midwire
