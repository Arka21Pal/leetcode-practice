# [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)

> A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

> Given a string `s`, return `true` *if it is a* ***palindrome****, or* `false` *otherwise*.

## My solution 1

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        # "isalnum" is a method to check if alphanumeric characters exist
        s = ''.join(ch for ch in s if ch.isalnum())
        # Converting everything to lowercase
        s = s.lower()
        # Checking for a palindrome
        if s == s[::-1]:
            return True
        else:
            return False
```

## My solution 2

Copied from: https://leetcode.com/problems/valid-palindrome/discuss/1534623/Python-96%2B%2B-Faster-Solution-36ms

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        # Empty string to return later
        p = ""
        for i in s:
            # Checking if "i" is an alphanumeric character
            if i.isalnum():
                # Add the lowercase value of "i" to empty string "p"
                p = p + i.lower()
        # Return "True" if palindrome, or "False" if not
        return p == p[::-1]
```

# Resources

- https://www.delftstack.com/howto/python/remove-non-alphanumeric-characters-python/
- https://www.geeksforgeeks.org/isupper-islower-lower-upper-python-applications/
