---
title: "Problem 6"
date: 2020-03-23T00:00:18+01:00
draft: false
---

> The sum of the squares of the first ten natural numbers is 385. The square of the sum of the first ten natural numbers is 3025. Hence the difference between the sum of the squares of the first ten natural numbers and the square of the sum is 3025−385=2640
>
> Find the difference between the sum of the squares of the first one hundred natural numbers and the square of the sum.

The problem is very straightforward. We write a function to calculat the sum of squares of first n numbers and another function to calculate the square of the sum of first n natural numbers.

Using the standard formulas for sums, we can reduce runtime to O(1).

```python
def sum_of_squares(n):
    return n * (n + 1) * (2 * n + 1) / 6

def sum_n_squared(n):
    total = n * (n + 1) / 2
    return total**2
```

We now plug the value n = 100 in our functions to obtain desired result.

```python
sum_squares_100 = sum_of_squares(100)
sum_100_squared = sum_n_squared(100)
print(sum_100_squared - sum_squares_100)

25164150.0
```
