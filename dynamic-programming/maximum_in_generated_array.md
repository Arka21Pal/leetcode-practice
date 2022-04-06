# [1646. Get Maximum in Generated Array](https://leetcode.com/problems/get-maximum-in-generated-array/)

> You are given an integer n. A 0-indexed integer array nums of length n + 1 is generated in the following way:
>
> - `nums[0] = 0`
> - `nums[1] = 1`
> - `nums[2 * i] = nums[i] when 2 <= 2 * i <= n`
> - `nums[2 * i + 1] = nums[i] + nums[i + 1] when 2 <= 2 * i + 1 <= n`
>
> Return the maximum integer in the array nums.

Very easy problem, just need to iterate through numbers until we reach the limit, whilst adding the numbers to the list. Then, return maximum.

## Solution

```python
class Solution:
    def getMaximumGenerated(self, n: int) -> int:

        # Handle the edge-case
        if n==0: return 0

        # Create an array to use as a stack
        nums = [0]*(n+1)
        nums[1] = 1

        # Define variables as a placeholder
        # To be iterated in the loop
        i = 1
        b = 2
        c = 3

        # Present condition that neither variable will accept elements outside the loop
        while (b <= n) and (c <= n):
            # print(i)

            # Utilise the formulae given in the problem to compute numbers for their respective indices
            nums[b] = nums[i]
            nums[c] = nums[i+1] + nums[i]

            # Increment the main index and the corresponding variables
            i += 1
            b = (2*i)
            c = (2*i) + 1

        # Return the maximum number from the list
        return max(nums)
```

## Some other notable solutions:
- Meme solution: https://leetcode.com/problems/get-maximum-in-generated-array/discuss/1754391/Python-O(1)-solution
- https://leetcode.com/problems/get-maximum-in-generated-array/discuss/1587108/Python-3-O(n)
- https://leetcode.com/problems/get-maximum-in-generated-array/discuss/1771672/Python-or-Brute-Force-Approach-or-SImple-or-Generating-complete-array
- https://leetcode.com/problems/get-maximum-in-generated-array/discuss/1889734/Python
