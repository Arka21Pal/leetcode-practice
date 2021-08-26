# Convert roman numerals to integers

Link: https://leetcode.com/problems/roman-to-integer/

`s` (the input) will be between [0, 3999]

## My solution:

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        val = {'I':1, 'V':5, 'X':10, 'L':50, 'C':100, 'D':500, 'M':1000}
        l = len(s)
        total = 0
        for i in range(1, l):
            if val[s[i-1]] < val[s[i]]: # Comparing the current element with the previous element
                #Looking at the next step (else block), we are adding val[s[i-1]], so we need to subtract twice.
                total = total + val[s[i]] - (val[s[i-1]])*2             
            else:
                total = total + val[s[i]]
                # And here, we just add everything
        total = total + val[s[0]] # This is an extra step I'm having to do because I'm looping in range(1, l), without which the loop terminates (if i=0, s[i-1] doesn't exist).
        return total
```

## The solution from where I copied the concept:

[Link](https://leetcode.com/problems/roman-to-integer/discuss/1298123/Python3-Super-fast-than-99)

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        letters = list(s)
        romans = {'I':1, 'V':5, 'X':10, 'L':50, 'C':100, 'D':500, 'M':1000}
        sum_let = 0
        prev = None
        for lets in letters:
            if prev is not None and romans[prev] <  romans[lets]:
                sum_let+=(romans[lets]-(romans[prev]*2))
            else:
                sum_let+=romans[lets]
            prev = lets
        return sum_let
```
