---
title: "Problem 9"
date: 2020-03-26T12:47:10+01:00
draft: false
---

> A Pythagorean triplet is a set of three natural numbers, a < b < c, for which,
> a^2 + b^2 = c^2
> For example, 32 + 42 = 9 + 16 = 25 = 52.
>
> There exists exactly one Pythagorean triplet for which a + b + c = 1000.
> Find the product abc.

```python
a = 375
b = 200
c = 425

assert(a**2 + b**2 == c**2)
assert(a + b + c == 1000)
```
