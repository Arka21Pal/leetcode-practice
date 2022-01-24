# [Ransom Note](https://leetcode.com/problems/ransom-note/)

> Given two strings `ransomNote` and `magazine`, return `true` *if* `ransomNote` *can be constructed from* `magazine` *and* `false` *otherwise*.
>
> Each letter in magazine can only be used once in `ransomNote`.

## Solution

Shamelessly copied from: https://leetcode.com/problems/ransom-note/discuss/1658558/Python-99.91-faster-99.98-less-space

```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:

        # Keep only unique elements of ransomNote
        rn_set = set(ransomNote)
        for i in rn_set:
            # Check for the count of a particular element from both "ransomNote" and "magazine"
            # If "magazine" has a lesser count, obviously we cannot form "ransomNote" from it
            if ransomNote.count(i) > magazine.count(i):
                return False
        return True
```
