---
title: "Problem 1"
date: 2020-03-18T15:12:07+01:00
draft: false
---

## Multiples of 3 and 5

> If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9.
> The sum of these multiples is 23.
> Find the sum of all the multiples of 3 or 5 below 1000.

The problem can be reduced to an arithmetic series and solved in O(1).

We can use a simple function to calculate the sum of an arithmetic series using the
formula:

Sum of n terms of AP = (n/2) \* [2a + (n – 1)d]
where a is the first term and d is the common difference.

At this stage, however, use this formula directly because we do not know the value of n.

We first write a simple function to calculate the value of n by finding the last term

```python
def find_n(a: int, d: int, end: int) -> int:
    return 1 + ((end - a - 1) // d) #adding 1 to account for the first term
```

Now that we know the value of n, we can simply plug the values in our AP sum formula to calculate the result.
Here is our function to calculate the sum of an AP:

```python
def sum_of_AP(a: int, d: int, end: int):
    n = find_n(a, d, end)
    return (n / 2) * (2 * a + (n - 1) * d)
```

In the range 1 to 1000, we need to calculate:
the sum of multiples of 3 + the sum of multiples of 5 - the sum of multiples of 15.

We subtract the sum of multiples of 15 to correct for double counting,
first when adding sum of 3s and second when adding the multiples of 5 to obtain final result.

```python
def sum_3_5_multiples():
    return sum_of_AP(0, 3, 1000) + sum_of_AP(0, 5, 1000) - sum_of_AP(0, 15, 1000)

print(sum_3_5_multiples())
```

    233168.0
