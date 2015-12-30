---
layout: post
title:  "Introduction to Binary and Hexadecimal"
date:   2015-12-29 19:00:25 -0800
categories: coding
---

This is a work in progress.

You're probably not reading this guide because you want to understand binary or hexadecimal. Realistically,
you're here because you are trying to understand something else, like Unicode vs. UTF-8. This guide
will give you a crash course on binary and hex.

Prerequisites
===
This guide briefly uses vim.

- Knowledge of [vim](http://www.vim.org/download.php) (I'll write a guide about this later)


Intro to Binary
===
What's the deal with binary?

<img src="/assets/binary.jpg" width="400">

Oh, those 0's and 1's are oh-so-undecipherable! Or are they? We'll try to demystify them a bit in
this section.

At some level, all computer data is stored as binary. The root "bi" means "two", because in binary, there
are only two valid values for representing numbers: zero (0) and one (1). Consider that in Arabic numerals,
we count using decimal, ("dec" means 10, think "December", except without two random months introduced by Caesar), also known as "base-10":

{% highlight bash %}
00
01
02
03
04
05
06
07
08
09
10
11
...
{% endhighlight %}

This is called "base-10" because there are 10 possible values for a single "digit". Binary only has 2 possible values. Thus, binary number strings tend to be longer. For instance, counting to 11, the
same example as above, looks like this in binary:

{% highlight bash %}
0000
0001
0010
0011
0100
0101
0110
0111
1000
1001
1010
1011
{% endhighlight %}

Can you see the pattern? If not, let this illustration roughly explain how to convert binary numbers into decimal numbers:

IKAI FILL IN A DRAWING OR DOODLE HERE LATER

Binary is good for computers, because it's simple to represent each digit place as either "on" or "off",
"true" or "false". This has various advantages that are outside the scope of this guide.



Intro to Hexadecimal
===