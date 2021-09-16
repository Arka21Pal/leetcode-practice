# Remove element

Quite a bit simpler than the `remove-duplicates` question, but similar.

> Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in `nums` [in-place](https://leetcode.com/problems/remove-element/). The relative order of the elements may be changed.

## My solution

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        while True:
            try: nums.pop(nums.index(val))
            except: break
        return len(nums)
```

## Random solution:

*Link*: https://leetcode.com/problems/remove-element/solution/197569

```python
class Solution:
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        count = 0
        for i in range(len(nums)):
            if nums[i] != val :
                nums[count] = nums[i]
                count +=1
        return count
```
