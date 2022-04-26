# [349. Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/)

> Given two integer arrays `nums1` and `nums2`, return *an array of their intersection*. Each element in the result must be **unique** and you may return the result in **any order**.

## Solution

Copied from: https://leetcode.com/problems/intersection-of-two-arrays/discuss/1975746/Python-One-liner-Set-Intersection-Operation

```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        return list(set(nums1)&set(nums2))
```

## Another solution

Copied from: https://leetcode.com/problems/intersection-of-two-arrays/discuss/1975126/Python-Very-Easy-solution-using-Sets

```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        answer = []
        for i in set(nums1):
            if i in set(nums2):
                answer.append(i)
        return answer
```
