# A medium level problem. I have shamelessly copied the solution and implemented it myself, with very little success.

## My solution

```python
class Solution:
    def intToRoman(self, num: int) -> str:
        val = {1000:'M', 900:'CM', 500:'D', 400:'CD', 100:'C', 90:'XC', 50:'L', 40:'XL', 10:'X', 9:'IX', 5:'V', 4:'IV', 1:'I'} 
        number = ''
        for i,j in val.items():
            number = number + (num//i) * j # We're dividing the input by i, and then multiplying it with the respective letter j.
            num = num%i # Then, we push the remainder of the division between num and i.
        return number
```

## The solution I shamelessly copied:

[Link](https://leetcode.com/problems/integer-to-roman/discuss/1103010/Clean-and-Correct-Python-Solution)

```python

class Solution:
    def intToRoman(self, num: int) -> str:

        vals = [ 1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1 ]
        romans = [ "M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I" ]

        res=''

        for i,v in enumerate(vals):

            res += (num//v) * romans[i];
            num %= v

        return res
```
