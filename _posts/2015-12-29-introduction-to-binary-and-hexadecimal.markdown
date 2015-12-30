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

#### What's the deal with binary?

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

TODO IKAI FILL IN A DRAWING OR DOODLE HERE LATER

Binary is good for computers, because it's simple to represent each digit place as either "on" or "off",
"true" or "false". This has various advantages that are outside the scope of this guide. Without going
too much into binary math, here's what addition would look like in binary:

TODO IKAI FILL IN A DRAWING OR DOODLE HERE LATER ABOUT ADDITION IN BINARY

This sort of math is actually very easy for computers to process using "bitwise" operators. You know
bitwise operators? How programming languages have the single `|` or single `&`? This is the sort
of thing they are used for. There's one interesting properties of binary numbers: if you add a 0 to
the least significant bit (we'll cover "bits" in the next section), that is, the lowest value "digit",
you double the number. See the following chart:

{% highlight bash %}
1     => 1
10    => 2
100   => 4
1000  => 8
10000 => 16
{% endhighlight %}

If these numbers look familiar, that's because this is how computer scientists think: in terms of doubling.
An alternative representation is powers of 2: `2**1`, `2**2`, `2**3`, and so forth. Decimal numbers have
a related property:

{% highlight bash %}
1
10
100
1000
10000
{% endhighlight %}

Adding a zero to the end of the number multiples the value by 10 in base-10. Make sense? The `N` in
"base-N" tells you how much you are effectively multiplying the number by when you add a 0 to the end.

*Bonus factoid:* multiplying a number by 10 is often referred to as "increasing an order of magnitude".
To remember this, for us Californians, remember that [earthquakes are often referred to by their "order
of magnitude"](https://en.wikipedia.org/wiki/Richter_magnitude_scale) - a 7.0 earthquake has
10 times more "shaking power" (SORRY, I'M NOT A GEOLOGIST) than a 6.0 earthquake.

#### Bits and bytes

A single place in binary is called a "bit". 8 bits is called a "byte". How does this relate to programming?
Suppose you create an integer. A 32-bit that is all 1s is the "largest" value you can assign in binary:

`11111111 11111111 11111111 11111111`

That means the maximum value an integer can have is `4294967295`, according to our [binary to decimal converter](http://www.binaryhexconverter.com/binary-to-decimal-converter). But wait! Why is the maximum
integer value `2147483647`, [according to Wikipedia](https://en.wikipedia.org/wiki/2147483647_(number))?
That's because this number is the maximum _signed_ integer, which includes decimals. The maximum
unsigned integer is still `4,294,967,295`. Thanks [Wikipedia, again](https://en.wikipedia.org/wiki/32-bit)!
Representing negative numbers is outside the scope of this guide. If you're interested, here's [Cornell's
guide to two's complement](https://www.cs.cornell.edu/~tomf/notes/cps104/twoscomp.html).

Why isn't a megabyte exactly 1 million bytes? Why is it 1048576 bytes? Because this is 1024 times 1024.
1024 is 2 to the 10th power, which in binary is 1 followed by ten 0s.


Intro to Hexadecimal
===