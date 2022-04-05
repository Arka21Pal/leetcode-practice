# [392. Is Subsequence](https://leetcode.com/problems/is-subsequence/)

> Given two strings `s` and `t`, return `true` *if* `s` *is a* ***subsequence*** *of* `t`, *or* `false` *otherwise*.
>
> A **subsequence** of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., `"ace"` is a subsequence of `"abcde"` while `"aec"` is not).

The idea is again simple to understand, but a little tricky to implement. We need to compare the values of the elements in `s` and `t`, and check if the order of elements in `s` matches that in `t`. In this solution, this is achieved by checking the elements by each respective index. Checking the order is generally a troublesome situation, but this is easily done here.

## Solution

Copied from: https://leetcode.com/problems/is-subsequence/discuss/1881665/Python-two-pointer-solution

```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:

        # Define both pointers as zero to start from the beginning
        p1=p2=0

        # Checking if both pointers are within bounds, which is essential to checking the order
        while p1<len(s) and p2<len(t):

            # If the elements with the respective indexes match
            # Increment both pointers by 1
            if s[p1]==t[p2]:
                p1+=1
                p2+=1
            # If not, only increment "t"'s pointer by 1
            # This helps prevent any previous element from producing a false positive
            else:
                p2+=1

        # Return True if we reached till the end of "s"
        return p1==len(s)
```
