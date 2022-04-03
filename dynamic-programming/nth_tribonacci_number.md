# [1137. N-th Tribonacci Number](https://leetcode.com/problems/n-th-tribonacci-number/)

<blockquote>
The Tribonacci sequence T<sub>n</sub> is defined as follows:

T<sub>0</sub> = 0, T<sub>1</sub> = 1, T<sub>2</sub> = 1, and T<sub>n+3</sub> = T<sub>n</sub> + T<sub>n</sub>+1 + T<sub>n</sub>+2 for n >= 0.

Given n, return the value of T<sub>n</sub>.
</blockquote>

Very simple, simply cache the last three values and keep appending them to the list (in my case), and return the final value after you've reached it (n).

## Solution

```python
class Solution:
    def tribonacci(self, n: int) -> int:

        # Define a list as a cache
        values = [0, 1, 1]

        for i in range(3,n+1):

            # Keep appending the sum of the last three values, according to the formula provided to us
            values.append(values[i-3] + values[i-2] + values[i-1])

        # Return the last value as the answer
        return values[n]
```

## Other solutions
- https://leetcode.com/problems/n-th-tribonacci-number/discuss/1877659/Python-DP-faster-than-98
- https://leetcode.com/problems/n-th-tribonacci-number/discuss/1896216/Python-easy-solution-for-beginners
