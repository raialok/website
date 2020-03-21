---
title: "Problem 5"
date: 2020-03-21T19:44:48+01:00
draft: true
---

> 2520 is the smallest number that can be divided by each of the numbers from 1 to 10 without any remainder.
> What is the smallest positive number that is evenly divisible by all of the numbers from 1 to 20?

We first write a simple function to generate all prime factors of a given number.

```python
def prime_factors(n):
    factors = {1: 1}
    divisor = 2
    while n > 1:
        if n % divisor == 0:
            if divisor in factors:
                factors[divisor] += 1
            else:
                factors[divisor] = 1
            n /= divisor
        else:
            divisor += 1
    return factors
```

We now generate a list containing all factors of numbers from 1 to 20.

```python
factors_1_to_20 = []

for i in range(1, 21):
    factors_1_to_20.append(prime_factors(i))
```

We need to find the highest power of each unique factor across all dictionaries in this list.

```python
def gcd_factors(lst):
    highest_powers = {}
    for aDict in lst:
        for (k,v) in aDict.items():
            if k not in highest_powers or highest_powers[k] < v:
                highest_powers[k] = v
    return highest_powers

gcd_factors_1_20 = gcd_factors(factors_1_to_20)
```

Now, we can use the highest powers of each unique factor to generate the Least
Common Multiple of the range from 1 to 20.

```python
def lcm(aDict):
    current_lcm = 1
    for (k, v) in aDict.items():
        current_lcm *= (k ** v)
    return current_lcm

generate_gcd(gcd_factors_1_20)
```

The entire solution can be condensed into one function:

```python
def find_gcd(start, end):
    factors = []
    for i in range(start, end+1):
        factors.append(prime_factors(i))
    return generate_gcd(gcd_factors(factors))

print(find_gcd(1, 20))
232792560
```
