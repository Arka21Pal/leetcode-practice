# [509. Fibonacci Number](https://leetcode.com/problems/fibonacci-number/)

> The **Fibonacci numbers**, commonly denoted `F(n)` form a sequence, called the **Fibonacci sequence**, such that each number is the sum of the two preceding ones, starting from `0` and `1`. That is,
>
```
F(0 = 0, F(1) = 1
F(n) = F(n - 1) + F(n - 2), for n 1.
```
>
> Given `n`, calculate `F(n)`.

I've put in multiple submissions for this extremely easy problem, I'll show the fastest one here.

The idea is quite simple: A fibonacci number is simply the sum of the two previous fibonacci numbers. That is, `F(n) = F(n-1) + F(n-2)`. This is very easy to make into a program. The simplest way would be store values in a list, like a cache, and call them from there.

## Solution

Copied from: https://leetcode.com/problems/fibonacci-number/discuss/1890931/python-4-solutions

```python
class Solution:
    def fib(self, n: int) -> int:

        # The list acting as a cache
        cache = [0,1]
        for i in range(2,n+1):

            # Append the values according to the Fibonacci formula shown in the description
            cache.append(cache[i-1] + cache[i-2])

        # Return the requested value
        return cache[n]
```

For reference: https://leetcode.com/problems/fibonacci-number/discuss/1891327/Python-Solution-or-Recursive-or-Two-Methods-NaiveAuxillary-Storage

Great recursive method.
