# [852. Peak Index in a Mountain Array](https://leetcode.com/problems/peak-index-in-a-mountain-array/)

> Given an integer array arr that is **guaranteed** to be a mountain, return any `i` such that `arr[0] < arr[1] < ... arr[i - 1] < arr[i] > arr[i + 1] > ... > arr[arr.length - 1]`.

Super easy binary search problem. It's just that the condition for returning the middle element are slightly different (as is expected as they can change from question to question).

## Solution

```python
class Solution:
    def peakIndexInMountainArray(self, arr: List[int]) -> int:

        # Defined start and end
        start = 0
        end = len(arr) - 1

        while start <= end:

            # Defined mid
            mid = start + (end - start)//2

            # The condition that changed slightly, as this was required from the question (basically, find index of biggest element)
            if (arr[mid] > arr[mid + 1]) and (arr[mid] > arr[mid - 1]):
                return mid

            # If not, increment start
            if (arr[mid] < arr[mid + 1]):
                start = mid + 1

            # Or, decrement end
            else:
                end = mid - 1

```

```python
class Solution:
    def peakIndexInMountainArray(self, arr: List[int]) -> int:

        # Easiest, direct solution
         return arr.index(max(arr))
```
