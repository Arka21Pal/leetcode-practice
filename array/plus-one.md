# Plus one

> You are given a **large integer** represented as an integer array `digits`, where each `digits[i]` is the `i^th` digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading `0`'s.

> Increment the large integer by one and return *the resulting array of digits*.

## My solution
This solution scored better than the other solution of mine.
```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:

        # Get the integer from the array
        string = ""
        for i in digits:
            string = string + str(i)
        num = int(string)

        # Make a new list, and put the new number in there after incrementing it by one
        new_list = []
        for i in str(num+1):
            new_list.append(i)

        return new_list
```

## My solution 2

```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:

        # Actually, I copied this from another answer, but this just did what I've done in one line
        return [int(i) for i in str(int("".join([str(x) for x in digits]))+1)]
```

## Amazing Solution

```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        for i in range(len(digits)-1, -1, -1):
            if digits[i] != 9:
                digits[i] += 1
                return digits
            else:
                while digits[i] is 9:
                    digits[i] = 0
                    i -= 1
                if i == 0:
                    digits[i] += 1
                    return digits
                if i == -1:
                    digits.insert(0, 1)
                    return digits
                else:
                    digits[i] += 1
                    return digits
```

## Amazing Solution 2

```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        length = len(digits) - 1
        while digits[length] == 9:
            digits[length] = 0
            length -= 1
        if(length < 0):
            digits = [1] + digits
        else:
            digits[length] += 1
        return digits
```
