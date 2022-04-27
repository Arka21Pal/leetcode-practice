# [367. Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square/)

> Given a **positive** integer *num*, write a function which returns True if *num* is a perfect square else False.

Simple Binary Search problem. Just check if the square of the element in the middle (between the start and end limits, which we will amend in a loop) matches the value required. If the value of the square of "mid" is less than "num", amend start. Otherwise, amend "end".

## Solution

Copied from: https://leetcode.com/problems/valid-perfect-square/discuss/1967878/Easy-Python-solution

```python
class Solution:
    def isPerfectSquare(self, num: int) -> bool:
        start = 0
        end = num

        # Declaring loop to amend "start" and "end"
        while start <= end:
            # Calculate "mid"
            # Important to add "start" and then subtract half of it in case of odd numbers
            mid = start + (end - start)//2
            if (mid ** 2) == num:
                return True
            elif (mid ** 2) < num:
                # Amend "start"
                start = mid + 1
            # Amend "end"
            else: end = mid - 1
        return False
```
