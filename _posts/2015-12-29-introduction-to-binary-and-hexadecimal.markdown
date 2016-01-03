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

#### What's the deal with hexadecimal?
In the way that we (humans) generally use base-10 and binary is base-2, hexadecimal is base-16. Since there
aren't enough Arabic/base-10 numerals to go to 16, past 9, the letters A-F (case insensitive) are used.
Counting 0 to 20 looks like this:

{% highlight bash %}
0  => 00
1  => 01
2  => 02
3  => 03
4  => 04
5  => 05
6  => 06
7  => 07
8  => 08
9  => 09
10 => 0A
11 => 0B
12 => 0C
13 => 0D
14 => 0E
15 => 0F
16 => 10
17 => 11
18 => 12
19 => 13
20 => 14
...
255 => FF
{% endhighlight %}

See the pattern? It's a bit misleading to see numbers such as `14` in Hexadecimal. One more note:
in more representations of hexadecimal, there are an even number of digits. That is, we would not
see values such as `AAA`, we would most likely see this value printed as `0AAA` or `0A AA`. The space
is purely for visual parsing.

#### Hexadecimal looks familiar!

Have you written HTML before? CSS? You've probably worked with hexadecimal. Have you ever specified an
HTML color using a value like `#FFFFFF`, `#000000`, or something weirder like `1DA4C6`? This is a
hexadecimal value! Check out the [HTML color picker here](http://html-color-codes.info/).



The value #000000 represents 3 values: 0 red, 0 green and 0 blue, which equals black. The "opposite" of
that value is `#FFFFFF`, which is 255 red, 255 green and 255 blue. All of the colors in HTML can be
specified with 256 * 256 * 256 possible values, or 16.7 million different colors.

#### Relationship between hexadecimal and binary

It is much easier to convert between hexadecimal and binary than it is to convert between either of
those bases and straight base-10 decimal. The reason for this is that hexadecimal is base-16, which
is a power of 2. Every hexadecimal value translates directly to a binary value:

{% highlight bash %}
0  => 00 => 0000 0000
1  => 01 => 0000 0001
2  => 02 => 0000 0010
3  => 03 => 0000 0011
4  => 04 => 0000 0100
5  => 05 => 0000 0101
6  => 06 => 0000 0110
7  => 07 => 0000 0111
8  => 08 => 0000 1000
9  => 09 => 0000 1001
10 => 0A => 0000 1010
11 => 0B => 0000 1011
12 => 0C => 0000 1100
13 => 0D => 0000 1101
14 => 0E => 0000 1110
15 => 0F => 0000 1111
16 => 10 => 0001 0000
17 => 11 => 0001 0001
18 => 12 => 0001 0010
19 => 13 => 0001 0011
20 => 14 => 0001 0100
...
255 => FF => 1111 1111
{% endhighlight %}

If you look at the chart above, each possible hexadecimal value `0` to `F` maps directly to a binary
value between `0000` and `1111`. That means that instead of having to do mental math to convert
between hexadecimal and binary, it is as simple as looking up each value in a table and directly
converting, or simply memorizing which hex value equals which binary value.

Binary and hexadecimal in files
===

At some level, all computer values map to 0s and 1s. This includes files on disk. If I create a file
that contains the following contents and save it as `test.txt`:

`The quick brown fox jumps over the lazy dog.`

I can view it in hex in vim by entering hexadecimal mode by hitting escape and typing:

`:%!xxd`

The file now looks like this:

```
0000000: 5468 6520 7175 6963 6b20 6272 6f77 6e20  The quick brown
0000010: 666f 7820 6a75 6d70 7320 6f76 6572 2074  fox jumps over t
0000020: 6865 206c 617a 7920 646f 672e 0a         he lazy dog..
```

The left side shows first the character position followed by a colon, then the hex values of
the characters in the file. Lower case `b` is the value `62`, whereas lower case `a` is the value
`61`.

To view this file as binary, use this command in vim:

`:%!xxd -b`

The file looks like this:

```
0000000: 01010100 01101000 01100101 00100000 01110001 01110101  The qu
0000006: 01101001 01100011 01101011 00100000 01100010 01110010  ick br
000000c: 01101111 01110111 01101110 00100000 01100110 01101111  own fo
0000012: 01111000 00100000 01101010 01110101 01101101 01110000  x jump
0000018: 01110011 00100000 01101111 01110110 01100101 01110010  s over
000001e: 00100000 01110100 01101000 01100101 00100000 01101100   the l
0000024: 01100001 01111010 01111001 00100000 01100100 01101111  azy do
000002a: 01100111 00101110 00001010                             g..
```

If you take the time to map the binary characters to hex characters (don't do it, it's boring), you'll
see that each of the hex values maps directly to binary values. `01010100` in the first 8 bits maps
directly to `54` in hex, just like in the chart above on this page.

Summary
===

Thanks for reading all this. This information becomes very useful very quickly in programming, as we will
demonstrate in future posts. Thanks for sticking with it! Here is a math kitty.

![Math kitty](http://www.mathfunny.com/images/kitty-math-book-boring.jpg)



