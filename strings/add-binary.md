# Add Binary

> Given two binary strings `a` and `b`, return their sum as a binary string.

## My solution

```python
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        # Convert the binary strings to integers
        # Add them
        # Convert the sum into binary again
        # Show the string from after the first two characters
        return bin(int(a,2) + int(b,2))[2:]
```

## Copied solution

```python
class Solution:
    def addBinary(self, a: str, b: str) -> str:
        # Create pointers to start from the end of the strings
        i=len(a)-1
        j=len(b)-1

        # Empty string to return result
        result=""
        carry=0

        # Checking if all three variables exist
        while i>=0 or j>=0 or carry:

            # Creating a dummy variable to do all operations on
            # This variable will be equated to carry later on
            total=carry
            if i>=0:
                # Add the value of the number at index i of a
                total+=int(a[i])
                # Decrement the value of i to iterate further forward
                i-=1
            if j>=0:
                # Add the value of the number at index j of b
                total+=int(b[j])
                # Decrement the value of j to iterate further forward
                j-=1
            # The result should not have any number >= 2
            result+=str(total%2)
            # The carry shouldn't have any number >=2 either
            carry=total//2
        return result[::-1]
```

*Copied from*:
- [Easy Solution without using built-in library](https://leetcode.com/problems/add-binary/discuss/1405919/Easy-Solution-without-using-built-in-library)
- [linear time solution best and simple solution](https://leetcode.com/problems/add-binary/discuss/1456200/python3-c%2B%2B-linear-time-solution-best-and-simple-solution)

## Resources
- [FACEBOOK - ADD BINARY (LeetCode)](https://www.youtube.com/watch?v=tRpusgdZxrE)
