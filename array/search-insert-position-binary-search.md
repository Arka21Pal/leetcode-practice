# [Search Insert Position](https://leetcode.com/problems/search-insert-position/)

> Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

Seemed like a simple problem until I discovered it was a binary search tree problem. Oh well.

## My solution

```python
class Solution:
    def searchInsert(self, nums: List[int], target: int) -> int:

        # code for the easier cases

        l = len(nums)
        if nums[0]>target:
            return 0
        if nums[-1]<target:
            return l

        # we will check if the middle element of the list is equal to our target
        # if it is greater, we will eliminate latter half of our list
        # if it is smaller, we will eliminate first half of the list
        # this will go on until both our pointers, left and right, converge; that's when we will return left

        left = 0
        right = l
        while left <= right:
            middle = (left + right)//2
            if target > nums[middle]:
                left = middle + 1
            if target < nums[middle]:
                right = middle - 1
            if target == nums[middle]:
                return middle
        return left
```

Wholly unoriginal solution. Every solution I saw in the discussion section used a `BST`, so I don't think I missed out on anything.

## Resources:
- [Easy Python Solution with Explanation](https://leetcode.com/problems/search-insert-position/discuss/1467870/Easy-Python-Solution-with-Explanation)
- [:=) Python Soln (Binary Search - Ceil)](https://leetcode.com/problems/search-insert-position/discuss/1471046/%3A)-Python-Soln-(Binary-Search-Ceil))

The first link in this section is very helpful, I took the comments in my code from this snippet.
