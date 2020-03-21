---
title: "Problem 4"
date: 2020-03-21T12:08:49+01:00
draft: false
---

> A palindromic number reads the same both ways.
> The largest palindrome made from the product of two 2-digit numbers
> is 9009 = 91 × 99.
>
> Find the largest palindrome made from the product of two 3-digit numbers.

A naive solution would be start check the products of a pair (i, j),
starting with i = 999, j = 999, and verifying if the product is a
palindrome.

The runtime for such a program, requiring two for loops, will be O(n²).

```python
def is_palindrome(num: int):
    num_str = str(num)
    # Checking if the string is equal to its reverse
    return num_str == num_str[::-1]
```

We now generate the products of all pairs of three digit numbers, check if the product is a palindrome, and select the largest such product. The strategy is naïve.

```python
def largest_three_digit_palin():
    for i in range(999, 99, -1):
        for j in range(999, 99, -1):
            product = i * j
            if is_palindrome(product):
                return product

print(largest_three_digit_palin())

580085
```

An alternative way would be to analyse the product. As the product must be a palindrome, it should be a six digit number of the form abccba or 100000a + 10000b + 1000c +100c + 10b + a.

Simplifying the product, it can be reduced to 11 (9091 a + 1000b + 100c). Knowing that out of the two three digit numbers p and q, one and only one must be a multiple of 11 we can simplify the search space by a factor of 11 even if the runtime remains O(n²).
