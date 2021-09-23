# [Sqrt(x)](https://leetcode.com/problems/sqrtx/)

Simple problem, find the `sqrt` of the provided input `x`, without any in-built operators like `**`. If the `sqrt` is a decimal, return an integer with the decimals truncated.

## My solution 1
Brute force solution, doesn't work very well and takes time.
```python
class Solution:
    def mySqrt(self, x: int) -> int:
        if x == 0: return 0
        i = 0
        while (i*i) <= x:
            i+=1
        return (i-1)
```

## My solution 2
Blatantly copied from other sources.
```python
class Solution:
    def mySqrt(self, x: int) -> int:

        # Define indices for binary search
        l = 0
        r = x

        # Define the condition, that if the right limit reaches the left limit
        while (r>=l):

            # Define m, the middle of the both indices
            m = l + (r-l)//2

            # Return m if we get an exact sqrt
            if (m*m) == x:
                return m
            # Decrement r if the square of midpoint reaches beyond the number
            if (m*m) > x:
                r = m - 1
            # Increment l if the square of midpoint is less than the number
            else:
                l = m + 1
        return r
```

## Resources:
- [96.36% faster, Binary-Search, Python, Easy-understanding](https://leetcode.com/problems/sqrtx/discuss/1367793/96.36-faster-Binary-Search-Python-Easy-understanding)
- [a binary search solution (28ms)](https://leetcode.com/problems/sqrtx/discuss/1414836/Python-a-binary-search-solution-(28ms))
- [Python solution using Binary Search](https://leetcode.com/problems/sqrtx/discuss/1468648/Python-solution-using-Binary-Search)
