# [746. Min Cost Climbing Stairs](https://leetcode.com/problems/min-cost-climbing-stairs/)

<blockquote>
You are given an integer array <code>cost</code> where <code>cost[i]</code> is the cost of <code>i<sup>th</sup></code> step on a staircase. Once you pay the cost, you can either climb one or two steps.

You can either start from the step with index <sup>0</sup>, or the step with index <sup>1</sup>.

Return <i>the minimum cost to reach the top of the floor</i>.
</blockquote>

The question can seem tricky because the user can either traverse in steps of 1 or 2. However, the solution is in the problem, in that the least value out of both steps will be used. Thus, use another stack as a cache, and store every possible value to reach every step. This is done by adding the cost of the current step (whilst traversing in a loop), and adding the least value out of the values of the two previous steps. Then, return the minimum value of the last two steps, as we could've used either of them.

This should now be easy to solve, even in steps of three.

## Solution

Copied from: https://leetcode.com/problems/min-cost-climbing-stairs/discuss/1832953/Python3-Dynamic-programming

```python
class Solution:
    def minCostClimbingStairs(self, cost: List[int]) -> int:

        # Defining the stack as a cache and the first two values (as they are constants defined in the question)
        n = len(cost)
        values = [0]*n
        values[0] = cost[0]
        values[1] = cost[1]

        # Now, fill in values by adding the cost of the current step with the minimum of the two previous steps
        for i in range(2,n):
            values[i] = min(values[i-1], values[i-2]) + cost[i]

        # Return the minimum of the last two steps in the cache as the answer
        return min(values[-1], values[-2])
```
