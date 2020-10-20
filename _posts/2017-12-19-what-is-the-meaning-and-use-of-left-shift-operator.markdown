---
layout: post
title:  What is the meaning and use of left shift operator 
date:   2017-12-19 03:41:37 +0000
---


<< is the left shift operator, and meets the needs of both logical and arithmetic shifts.

Left shift (<<)

Integers are stored, in memory, as a series of bits. For example, the number 6 stored as a 32-bit int would be:

`00000000 00000000 00000000 00000110`
Shifting this bit pattern to the left one position (6 << 1) would result in the number 12:

`00000000 00000000 00000000 00001100`
As you can see, the digits have shifted to the left by one position, and the last digit on the right is filled with a zero. You might also note that shifting left is equivalent to multiplication by powers of 2. So 6 << 1 is equivalent to 6 * 2, and 6 << 3 is equivalent to 6 * 8. A good optimizing compiler will replace multiplications with shifts when possible.