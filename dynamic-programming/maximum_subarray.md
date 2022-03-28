# Easy problem, find the contiguous subarray in an array which has the largest sum.

My first run in with a specific algorithm: 

Link: https://leetcode.com/problems/maximum-subarray/

## My solution:

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        
        # Handling the smaller ones - gave me serious trouble with all sorts of edge cases.
        if len(nums)<3:
            return max(max(nums), sum(nums))
        
        # Kind of a mix between GeeksForGeeks and the solution which is 90% faster than others.
        # Unfortunately I don't have a concrete reason for this, this was really trial-and-error.
        # Although it's kind of intuitive, I can't rely on that.
        
        # Excellent logic, current is (almost) always updated, while total is only updated if current > total
        
        total = nums[0]
        current = nums[0]
        
        for x in nums[1:]:
            if x + current > x: # If x and current are bigger than just x, increase the value of current
                current = current + x
            else:
                current = x
            if current > total: # If current actually becomes bigger than total, make total = current
                total = current
        return total
```

## Shamelessly copied from these sources:

- Link: https://leetcode.com/problems/maximum-subarray/discuss/1003537/Python3-Solution-90-Faster

```python
# For a detailed explanation of this solution, google Kadance's Algorithm
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        max_sum = float('-inf')
        current_sum = 0
        
        for num in nums:
            if num + current_sum > num:
                current_sum = num + current_sum
            else:
                current_sum = num
            
            if current_sum > max_sum:
                max_sum = current_sum
        
        return max_sum
```
- Link: https://leetcode.com/problems/maximum-subarray/discuss/1168649/python-3-O(n)-solution

>The idea is to add new elements to `total` from the first element, if `total` is positive, keep adding new elements to it, meanwhile updating the maximum `res`. If `total` is negative, abandon it and start a new `total`.

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        #
        res = float('-inf')
        total = 0
        for i in range(len(nums)):
            total += nums[i]
            res = max(res,total)
            if total < 0:
                total = 0
        return res
```

## References:

- https://www.geeksforgeeks.org/largest-sum-contiguous-subarray/
- [Kadane's Algorithm to Maximum Sum Subarray Problem](https://www.youtube.com/watch?v=86CQq3pKSUw)
