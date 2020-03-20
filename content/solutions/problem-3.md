---
title: "Problem 3"
date: 2020-03-20T3:12:07+01:00
draft: false
---

> The prime factors of 13195 are 5, 7, 13 and 29. What is the largest prime factor of the number 600851475143 ?

We write a function `find_smallest_factor` that takes a number (> 2) and finds the smallest prime factor, except for 1.

```python
def find_smallest_factor(n):
    for i in range(2, n):
        if n % i == 0:
            return i
    return n
```

Now, we write a function `factorise` that takes a number n,
finds its smallest prime factor i, divides the number n by i, and then
iteratively runs the process on the quotient until the quotient is 1.
We store all prime factors in a list and find the maximum value: 6857.

Runtime: O(n)

```python
def factorise(n):
    factors = []
    while n > 1:
        factor = find_smallest_factor(n)
        factors.append(factor)
        n = n // factor
    return factors


largest_factor = max(factorise(600851475143))
print(largest_factor)

6857
```
