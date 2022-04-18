# [17. Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

> Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent. Return the answer in **any order**.
>
> A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

Very difficult problem. The trick here is that, even if we have 3 or more lists which we need to combine, we can simply start by combining the first two and then keep multiplying each list with the previous list. Bad explanation, sorry.

## Solution

Copied from: https://leetcode.com/problems/letter-combinations-of-a-phone-number/discuss/1956882/Python-Simple-Recursion

```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:

        # Dictionary of digits to letters
        letters = {"2": "abc", "3": "def", "4": "ghi", "5": "jkl", "6": "mno", "7": "pqrs", "8": "tuv", "9": "wxyz"}

        if not digits:
            return []
        if len(digits) == 1:
            # If there's only one digit, the list will only contain letters corresponding to that digit
            return [letter for letter in letters[digits[0]]]

        # Recursively return the sum of letter and word by calling the main function again with a list reduced in size
        # Every time the function is called, remove the first digit from it so the combinations are not repeated
        return [letter + word for word in self.letterCombinations(digits[1:]) for letter in letters[digits[0]]]
```
