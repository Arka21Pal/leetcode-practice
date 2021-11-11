# Merge Sorted Array

> You are given two integer arrays `nums1` and `nums2`, sorted in `non-decreasing order`, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.
>
> Merge `nums1` and `nums2` into a single array sorted in `non-decreasing order`.

## My solution 1
Shamelessly copied from [Easy to understand :) Python](https://leetcode.com/problems/merge-sorted-array/discuss/1568990/Easy-to-understand-%3A)-Python)
```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        # Pop the redundant elements
        for i in range(n):
            nums1.pop()
        # Append all the elements from nums2 in nums1
        for i in nums2:
            nums1.append(i)
        # Sort everything
        nums1.sort()
```

## My solution 2
Copied from [16ms...98.84% faster.....very compact code in python](https://leetcode.com/problems/merge-sorted-array/discuss/1561312/16ms...98.84-faster.....very-compact-code-in-python)
```python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        # Substitute all elements from "n" to "m+n" in nums1 with elements from nums2
        nums1[m:n+m]=nums2[:n]
        nums1.sort()
```
Although I'm not very sure why we need `nums2[:n]`, I tried with just `nums2` on the RHS, the solution took 4 milliseconds more.
