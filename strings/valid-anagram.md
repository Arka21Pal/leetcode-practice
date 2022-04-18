# [Valid Anagram](https://leetcode.com/problems/valid-anagram/)

> Given two strings `s` and `t`, return `true` *if* `t` *is an anagram of* `s`, *and* `false` *otherwise*.
>
> An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

## My solution 1

Shamelessly copied from: https://leetcode.com/problems/valid-anagram/discuss/1712750/Simple-python-solution-easy

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # "Counter()" makes a dictionary with the elements and their counts
        m = collections.Counter(s)
        n = collections.Counter(t)
        return m == n
```

## My solution 2

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # The idea is that anagrams, when sorted, should be the same
        m = "".join(sorted(s))
        n = "".join(sorted(t))
        return m == n
```

## My solution 3

This, for some reason, is not working. I am certain, however, that it is a valid solution.

```python
class Solution:
    def isAnagram(s: str, t: str) -> bool:

        # Of course, anagrams can't have different lengths
        if len(s) == len(t):

            # Empty dictionary
            empty = {}

            # Counting the elements in "s"
            # If not present in "empty", initialise their value with 1
            for i in s:
                if i in empty: empty[i] += 1
                else: empty[i] = 1
            # And if elements from "t" are present in "empty", decrease value by 1
            # If they aren't present, "t" and "s" are not anagrams
            for i in t:
                if i in empty: empty[i] -= 1
                else: return False

            # If "t" and "s" are anagrams,
            # No letter should be left with a value more than 0
            for value in empty.values():
                if value: return False

            return True

        return False
```
