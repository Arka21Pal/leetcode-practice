# [Single Number](https://leetcode.com/problems/single-number/)

> Given a **non-empty** array of integers `nums`, every element appears *twice* except for one. Find that single one.

> You must implement a solution with a linear runtime complexity and use only constant extra space.

## My solution

Shamelessly copied from: https://leetcode.com/problems/single-number/discuss/1688459/Python-solution-with-dictionary

```python
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        # A normal dict will give out errors here, because I'm pushing values for keys which don't exist.
        new_dict = defaultdict(int)
        for i in nums:
            new_dict[i]  += 1
        # If a key is unique, it'll have the value of 1
        for j in new_dict:
            if new_dict[j] == 1:
                return j
```

## Resources

- https://www.geeksforgeeks.org/defaultdict-in-python/
