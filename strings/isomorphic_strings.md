# [205. Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/)

> Given two strings `s` and `t`, *determine if they are isomorphic*.
>
> Two strings `s` and `t` are isomorphic if the characters in `s` can be replaced to get `t`.
>
> All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character, but a character may map to itself.

Very easy logic, just create a spare dictionary and put individual characters in if they aren't present already. Then, check if the supposed key from the dictionary matches the current key found by traversing through the second string. If they don't match, return False.

## Solution:

Copied from: https://leetcode.com/problems/isomorphic-strings/discuss/1841091/Python-99.84-solution

```python
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:

        # Declare the dictionary and set
        d = dict()
        u = set()

        # Length of both strings is the same
        for i in range(len(s)):

            # If s[i] doesn not exist in the dictionary
            if s[i] not in d.keys():

                # If t[i] does not exist in the set defined for the characters
                # This step saves a lot of compute and memory, compared to when I was using d.values() to check for t[i]
                if t[i] not in u:

                    # Add the key and the value
                    d[s[i]] = t[i]
                    # Add the value to the dictionary
                    u.add(t[i])

                # Of course, if the key doesn't exist, but the value does, it means that the same value is being used for a different key
                # Return False in such a case
                else: return False

            # Or, if the value of the key doesn't match what is supposed to be the value, also return False
            # That means 2 keys with the same value are using different keys
            elif d[s[i]] != t[i]: return False
        return True
```






The idea to use a `set` instead of the values of the dictionary to check for `t[i]` was inspired by:

```python
class Solution:
    def isIsomorphic(self, s: str, t: str) -> bool:
        # use a hash map to do this

        hashMap = {} # of actual char in s to the mapped char to that matches t
        usedLetters = set()
        for i in range(len(s)):
            if s[i] not in hashMap:
                if t[i] in usedLetters:
                    return False
                hashMap[s[i]]=t[i]
                usedLetters.add(t[i])
            elif hashMap[s[i]]!=t[i]:
                return False
        return True
```

Another solution: https://leetcode.com/problems/isomorphic-strings/discuss/1878409/Python3-Simple-Solution
