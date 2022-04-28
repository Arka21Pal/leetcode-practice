# [744. Find Smallest Letter Greater Than Target](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)

> Given a characters array `letters` that is sorted in **non-decreasing** order and a character `target`, return *the smallest character in the array that is larger than* `target`.

Same as every other binary search problem, just define "start" and "end" limits, and then amend them according to the target, with the calculated "mid".

## Solution

Copied from: https://leetcode.com/problems/find-smallest-letter-greater-than-target/discuss/1964302/Python-oror-Simple-and-Clean-Binary-Search

```python
class Solution:
    def nextGreatestLetter(self, letters: List[str], target: str) -> str:

        # Define limits for the loop
        n = len(letters)
        start , end = 0, n

        # Loop
        while start < end:
            mid = (start + end)//2

            # Amend "end" if condition doesn't match
            if target < letters[mid]:
                end = mid
            # Amend "start"
            else: start = mid + 1

        return letters[start%n]
```
