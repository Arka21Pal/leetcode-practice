# [Climbing stairs](https://leetcode.com/problems/climbing-stairs/)

> You are climbing a staircase. It takes `n` steps to reach the top.
> Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?

Classic Dynamic programming question. I honestly have no idea how I can do this in a real interview.

# My solution
Shamelessly copied from [Python dp solution (memoization + tabulation)](https://leetcode.com/problems/climbing-stairs/discuss/1466644/Python-dp-solution-(memoization-%2B-tabulation))
```python
class Solution:
    def climbStairs(self, n: int) -> int:

        # No need to go further in if this is the case.
        if n<=2: return n

        # Declaring the array.
        dp=[0]*(n+1)
        dp[1]=1
        dp[2]=2

        # Starting from 3 because 1 and 2 are already defined.
        i = 3
        while i <= n:

            # The current step is the combination of the ways you can come from the previous steps.
            # As our only steps are 1 and 2, thus we can either come from a step directly under this one.
            # Or we could come from the step below the step directly under the current one.
            # i.e. i-1 and i-2
            # Thus, if we were allowed 1, 2, 3 steps, we would've done dp[i] = dp[i-1] + dp[i-2] + dp[i-3], and i would've started from 4.
            dp[i] = dp[i-1] + dp[i-2]
            i += 1
        return dp[n]
```

This is the tabulation version of the solution. I didn't understand the memoization method unfortunately.
## Resources
This approach was explained in this video: [GOOGLE CODING INTERVIEW QUESTION - CLIMBING STAIRS (LeetCode)](https://www.youtube.com/watch?v=uHAToNgAPaM)


# My solution 2
Again, shamelessly copied from [beats 99.86% beautiful short and simplest solution](https://leetcode.com/problems/climbing-stairs/discuss/1482459/beats-99.86-beautiful-short-and-simplest-solution)
```python
class Solution:
    def climbStairs(self, n: int) -> int:
        a,b = 0,1
        for i in range(n):
            a, b = b, a+b
        return b
```
However, I do not understand how he got away with using 0 and 1 instead of 1 and 2.

