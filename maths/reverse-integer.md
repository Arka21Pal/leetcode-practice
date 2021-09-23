# [Reverse Integer](https://leetcode.com/problems/reverse-integer/)

> Given a signed 32-bit integer `x`, return `x` *with its digits reversed*. If reversing `x` causes the value to go outside the signed 32-bit integer range `[-231, 231 - 1]`, then return `0`.

## My solution
Shamelessly copied from [Python3 Runtime: 24 ms, faster than 97.06% of Python3 online submissions for Reverse Integer](https://leetcode.com/problems/reverse-integer/discuss/1413065/Python3-Runtime%3A-24-ms-faster-than-97.06-of-Python3-online-submissions-for-Reverse-Integer).
```python
class Solution:
    def reverse(self, x: int) -> int:

        # Get the absolute (positive) value of x
        y = abs(x)
        n = 0

        # While y (i.e. positive x) exists
        while y:

            # Store the remainder of dividing y by 10, in a temporary variable
            temp = y%10

            # This is simply the quotient when dividing y by 10. This needed, because the new number at the units digit needs to be taken in the next iteration.
            # Alternatively, I could also do: y = y//10
            # However, this operation below is faster by 4 ms and uses 0.1 MB less ram, according to leetcode.
            y = (y-temp)//10

            # This is simply for the first iteration of the loop, when n=0.
            # Temp is the units digit of the current y. It makes sense to add that to n, because we will be returning n.
            if n==0:
                n=temp
            else:
                # Multiply the current number by 10, to make way for the new units digit, and then add the new units digit (which is temp).
                n = n*10 + temp
        if x<0:
            n = (-n)

        # Sticky condition. Checking x is of no use, we need to check for n.
        return n if n > -2**31 and n < 2**31-1 else 0
```

## My solution 2
This one converts the number to a string and back. Easy and naive solution.
```python
class Solution:
    def reverse(self, x: int) -> int:
        if x==0:
            return 0

        # Remove the negative sign and reverse the string
        reverse = int(str(x).replace('-','')[::-1])

        # Check if the reversed string matches conditions
        if reverse<(2**31-1):
            if x<0:
                return reverse*-1
            else:
                return reverse
        else:
            return 0
```
