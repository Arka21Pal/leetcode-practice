# [First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)

> Given a string `s`, *find the first non-repeating character in it and return its index*. If it does not exist, return `-1`.

## My solution

```python
class Solution:
    def firstUniqChar(self, s: str) -> int:

        # Random dictionary to hold elements and their counts
        go = {}

        # Iterating through the list
        for i in s:
            # Checking if the element has an existing count
            # If not, initialise a count
            if i in go:
                go[i] += 1
            else: go[i] = 1

        # Keys with a count of more than one are repeated
        # Just iterate through to find the first unrepeated key
        for i in go.keys():
            if go[i] == 1:
                return s.index(i)
        return -1
```
