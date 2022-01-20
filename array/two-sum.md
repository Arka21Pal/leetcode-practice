# [Two Sum](https://leetcode.com/problems/two-sum/)

> Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to* *`target`*.
>
> You may assume that each input would have ***exactly one solution***, and you may not use the *same* element twice.
>
> You can return the answer in any order.

## My solution 1 (brute force)

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        # Iterating through the list
        for i in range(len(nums)):
            # Iterating through the list for elements not already iterated through before (in the previous loop)
            for j in range(i+1, len(nums)):
                # If they add up, return the values
                if nums[i] + nums[j] == target:
                    return [i,j]
```

## My solution 2

Shamelessly copied from: https://leetcode.com/problems/two-sum/discuss/1696059/Hashtable%3A-56-ms-faster-than-91.94

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        # Empty dictionary
        dic = {}
        # Enumerating the list and then going over the values and indexes
        for key, value in enumerate(nums):
            # Calculating the difference between target and value
            # This can also be thought of as finding the number to add to existing value to reach target
            dif = target - value
            # And if the number to add (or the difference between target and existing value) exists in "dic" (empty dictionary)
            # Return the value
            if dif in dic:
                return[key,dic[dif]]
            # And if that doesn't work, simply add it to the dictionary
            dic[value] = key
```
