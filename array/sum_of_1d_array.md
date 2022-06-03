# [1480. Running Sum of 1d Array](https://leetcode.com/problems/running-sum-of-1d-array/)

> Given an array `nums`. We define a running sum of an array as `runningSum[i] = sum(nums[0]…nums[i])`.

> Return the running sum of `nums`.

All I'm doing is adding all of the previous elements with the next element. Just different ways to do it. Solution 3 has an elegant (but inefficient) one-liner.

## Solution 1

```python
class Solution:
    def runningSum(self, nums: List[int]) -> List[int]:
        n = len(nums)
        if n == 1:
            return nums
        
        s = nums[0]
        
        # Just keep adding the current element to the sum of the previous elements
        for i in range(1, n):
            s += nums[i]
            nums[i] = s
        
        return nums
```

## Solution 2

```python
class Solution:
    def runningSum(self, nums: List[int]) -> List[int]:
        n = len(nums)
        
        if n == 1:
            return nums
        
        # Using a separate array instead of editing nums
        s = [nums[0]]
        for i in range(1, n):
            s.append(nums[i] + s[i-1])
        return s
```

## Solution 3

Copied from: https://leetcode.com/problems/running-sum-of-1d-array/discuss/2104758/One-Liner-Python%3A-List-Comprehension-(Beginner-Friendly)

```python
class Solution:
    def runningSum(self, nums: List[int]) -> List[int]:
    
        # Add each element before (i+1) and return as one element of the final list inside which the process is enclosed
        return [sum(nums[:i+1]) for i in range(len(nums))]
```
