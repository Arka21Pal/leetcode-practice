# [2011. Final Value of Variable After Performing Operations](https://leetcode.com/problems/final-value-of-variable-after-performing-operations/)

> There is a programming language with only four operations and one variable `X`:
> - `++X` and `X++` **increments** the value of the variable `X` by `1`.
> - `--X` and `X--` **decrements** the value of the variable X by `1`.
> Initially, the value of `X` is `0`.

Just check which operator is being used in each step and increment and decrement accordingly.

## Solution 1

```python
class Solution:
    def finalValueAfterOperations(self, operations: List[str]) -> int:
        add = ["X++", "++X"]
        sub = ["X--", "--X"]
        x = 0
        for i in operations:
            if i in add: x += 1
            if i in sub: x -= 1
        return x
```

## Solution 2

```python
class Solution:
    def finalValueAfterOperations(self, operations: List[str]) -> int:
        x=0
        for i in operations:
            if "-" in i:
                x -= 1
            else:
                x += 1
        return x
```
