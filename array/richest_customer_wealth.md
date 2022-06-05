# [1672. Richest Customer Wealth](https://leetcode.com/problems/richest-customer-wealth/)

> You are given an `m x n` integer grid `accounts` where `accounts[i][j]` is the amount of money the `i^th` customer has in the `j^th` bank. Return *the* ***wealth*** *that the richest customer has*.

> A customer's wealth is the amount of money they have in all their bank accounts. The richest customer is the customer that has the maximum wealth.

Super simple, just the maximum of the sum of each column.

## Solution

```python
class Solution:
    def maximumWealth(self, accounts: List[List[int]]) -> int:

        # sum(accounts[i]) for the sum of every column
        # len(accounts) for the total number of rows
        return max(sum(accounts[i]) for i in range(len(accounts)))
```
