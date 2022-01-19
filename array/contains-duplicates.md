# [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)

> Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

## My solution 1

Copied implementation from: https://leetcode.com/problems/contains-duplicate/discuss/1698064/5-Different-Approaches-w-Explanations

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        # Empty stack.
        count = {}
        for i in nums:
            # Initialise count for previously non-existent elements as 0.
            if i not in count: count[i] = 0
            # Add one to existing entries.
            count[i] += 1
        for value in count.values():
            # If the count of an entry is more than one, it is repeated.
            if value > 1: return True
        return False
```

## My solution 2:

Copied from: https://leetcode.com/problems/contains-duplicate/discuss/1688485/Python-Solutionoror-Faster-than-95oror-Easy-understand

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        # "set()" basically return a tuple of distinct elements only.
        # Thus, if the length of the set is less than the original list, obviously an element (or more) has/have been repeated.
        if len(nums) > len(set(nums)): return True
        else: return False
```
