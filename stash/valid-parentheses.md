# Valid Parentheses

Given a string, determine if the string is valid.

> Input: s = "()[]{}"  
> Output: true

> Input: s = "([)]"  
> Output: false

*Link:* https://leetcode.com/problems/valid-parentheses/

## My solution

```python
class Solution:
    def isValid(self, s: str) -> bool:
        new = []
        if len(s) % 2 != 0: return False
        for i in s:
            if i == '(' or i == '[' or i == '{':
                new.append(i) # Append to the stack
            # Match and pop brackets
            elif i == ')' and len(new) != 0 and new[-1] == '(':
                new.pop()
            elif i == ']' and len(new) != 0 and new[-1] == '[':
                new.pop()
            elif i == '}' and len(new) != 0 and new[-1] == '{':
                new.pop()
            else: return False # If nothing matches, return False
        if len(new) != 0: return False # If length of stack is not zero, some bracket didn't match
        else: return True
```

## [Stack | Python | Simple | With Comments](https://leetcode.com/problems/valid-parentheses/discuss/1459641/Stack-or-Python-or-Simple-or-With-Comments)

```python
class Solution:
    def isValid(self, s: str) -> bool:
        out_dict = { '(':')', '[':']', '{':'}' }
        stack = []

        for char in s:
            if char in out_dict:
                stack.append(char)   #if opening bracket add into stack
            elif (not stack) or (char != out_dict[stack.pop()]): #if closing bracket map with the correct opening bracket
                return False
        return stack == [] #Check if all the opening brackets are closed
```

## Resources

- [FACEBOOK - VALID PARENTHESES (LeetCode)](https://www.youtube.com/watch?v=f8Jq8Ibg2Ys)
