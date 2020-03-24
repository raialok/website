---
title: "Problem 7"
date: 2020-03-24T10:39:22+01:00
draft: true
---

> By listing the first six prime numbers: 2, 3, 5, 7, 11, and 13, we can see that the 6th prime is 13.
> What is the 10 001st prime number?

```python
primes = [2]

def generate_primes(n):
    count = 1
    current = 2
    global primes
    while count < n:
        current += 1
        is_prime = True

        for i in primes:
            if current % i == 0:
                is_prime = False
                break

        if is_prime:
            primes.append(current)
            count += 1

generate_primes(10_001)
print(primes[-1])

104743
```
