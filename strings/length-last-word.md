# [Length of Last Word](https://leetcode.com/problems/length-of-last-word/)

Very simple problem, find the length of the last word in the string provided. This is very easy in Python because we have the `split()` method. I don't know how I would do this in Java, C, or bash for example.

## My solution

```python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:

        # The good thing about split() is that it takes white space as the default delimiter.
        return len(s.split()[-1])
```
