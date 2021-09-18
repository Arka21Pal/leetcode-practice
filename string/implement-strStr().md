# [Implement `strStr()`](https://leetcode.com/problems/implement-strstr)

Looks easy (and is actually quite easy to do in Python, from my second solution), but I'm a bit dumb so couldn't catch the idea sooner.

> Return the index of the first occurrence of `needle` in `haystack`, or `-1` if `needle` is not part of `haystack`.

> What should we return when `needle` is an empty string? This is a great question to ask during an interview.
> For the purpose of this problem, we will return 0 when `needle` is an empty string. This is consistent to C's `strstr()` and Java's `indexOf()`.

## My solution 1
I'm listing my solutions in chronological order, this is actually the slower solution.
```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        if needle == "":
            return 0
        if needle in haystack:
            for i in range(len(haystack)):
            
            # The line below is essentially saying that;
            # 1. Some letter in haystack should match the first letter of needle
            # 2. The length of haystack remaining after we've found such a letter should be greater than or equal to the length of needle
            # 3. Needle should start on i, (which means that i to i + len(needle) should match the string needle perfectly)
                if haystack[i] == needle[0] and len(haystack[i:]) >= len(needle) and haystack[i:i+len(needle)] == needle:
                    return i
        else:
            return -1
```

## My solution 2
This is the faster solution
```python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        if needle == "":
            return 0
        if needle in haystack:
            return haystack.index(needle)
        else:
            return -1
```
This is very easy to understand, tbh I didn't even know that it's possible to find the index of an arbitrary string inside another string in Python, but here we are.

### Disclaimer: Neither of these solutions are original, but they're easy, and I am too lazy to post links right now. 

## Resources:
- [KMP Algorithm for Pattern Searching](https://www.geeksforgeeks.org/kmp-algorithm-for-pattern-searching/)
