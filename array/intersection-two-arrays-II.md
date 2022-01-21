# [Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

> Given two integer arrays `nums1` and `nums2`, return *an array of their intersection*. Each element in the result must appear as many times as it shows in both arrays and you may return the result in **any order**.

## My solution 1

Copied from: https://leetcode.com/problems/intersection-of-two-arrays-ii/discuss/1706064/Simple-Python-solution-O(m)

```python
class Solution:
    def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:
        # Empty stack
        op = []
        # Iterating over all elements of "nums1" to find common elements
        # Doing that by checking if element exists in "nums2" in every step
        for i in nums1:
            if(i in nums2):
                # If a common element is found, add it to "op" and remove it from "nums2" 
                # This is to ensure that we get the correct number of elements
                op.append(i)
                nums2.remove(i)
        # Return answer
        return(op)
```

## My solution 2

Copied from: https://leetcode.com/problems/intersection-of-two-arrays-ii/discuss/1701554/Python-solution-with-HashMaps-(Easy)

```python
class Solution:
    def intersect(self, nums1: List[int], nums2: List[int]) -> List[int]:

        # Empty hashmap
        h1 = {}
        h2 = {}

        # Add all elements from "nums1" into "h1", and keep count by adding "1" every time they're in the loop
        # This is to check for repeated elements
        for i in nums1:
            if i in h1:
                h1[i] += 1
            else:
                h1[i] = 1

        # Same logic to check for repeated elements from "nums2" into "h2"
        for i in nums2:
            if i in h2:
                h2[i] += 1
            else:
                h2[i] = 1

        # get common keys (intersections)
        com = [x for x in h1 if x in h2]

        # for the intersections build answer
        ans = []
        for c in com:
            # Find the minimum number of times an element has been repeated between "nums1" and "nums2"
            # And append that element the specific number of times it's been repeated
            i = min(h1[c], h2[c])
            while i:
                ans.append(c)
                # Make sure to not run an infinity loop
                i -= 1

        return ans
```
