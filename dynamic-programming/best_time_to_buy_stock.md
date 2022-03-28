# [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

> You are given an array prices where `prices[i]` is the price of a given stock on the `i<sup>th</sup>` day.

> You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

> Return *the maximum profit you can achieve from this transaction*. If you cannot achieve any profit, return `0`.

Decent problem, not too hard, but my brain is just useless at this.

## My solution

Copied from: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/discuss/1657293/Python-canonical-solution.-Complexity%3A-O(N)O(1)

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        # Initialising a variable for cost.
        # No real reason to take prices[0] other than a few cases where considering the smallest value by default leads to a wrong result.
        cost = prices[0]
        profit = 0
        for i in prices[1:]: # Skipping the first element of the list as that is cost.
            # Correcting any problems by considering cost as the first element, by checking against every element.
            cost = min(i,cost)
            # Going with the aim of the problem, maximising profit by checking the difference of value and existing cost for every value.
            profit = max(profit, (i - cost))
        return profit
```
