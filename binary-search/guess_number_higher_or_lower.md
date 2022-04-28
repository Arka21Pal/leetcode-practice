# [374. Guess Number Higher or Lower](https://leetcode.com/problems/guess-number-higher-or-lower/)

Summary: using binary search, guess the number from the computer. A function "guess" is already defined which tells you if your guess if higher, lower or equal to the guess of the computer.

The concept is the same in most of the easy question of Binary Search: have a mid point, and amend the start and end with this midpoint, depending on the result you get.

## Solution

```python
# The guess API is already defined for you.
# @param num, your guess
# @return -1 if num is higher than the picked number
#          1 if num is lower than the picked number
#          otherwise return 0
# def guess(num: int) -> int:

class Solution:
    def guessNumber(self, n: int) -> int:
        # Limits defined for ease
        start = 1
        end = n

        while start <= end:
            # Midpoint defined
            mid = start + (end - start)//2
            if guess(mid) == 0:
                # If our guess matches the guess of the computer
                return mid
            if guess(mid) == -1:
                # If our guess is higher than the guess of the computer
                end = mid - 1
            if guess(mid) == 1:
                # If our guess is lower than the guess of the computer
                start = mid + 1

```
