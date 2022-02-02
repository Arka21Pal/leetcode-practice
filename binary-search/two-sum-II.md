# [167. Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

> Given a **1-indexed** array of integers `numbers` that is already ***sorted in non-decreasing order***, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

It is a very easy concept:\
There will be two pointers, one from the beginning and the other from the end of the list. Both of these will iterate through the list, the former forwards, whilst the latter, backwards. As if they are going to collide.
Every time, we will add up the values from the positions that these pointers hold. If the sum is greater than the target, the latter pointer will decrement once (getting closer to the centre). If the sum is lesser than the target, the former pointer will be incremented (closer to the centre). This will go on until the sum equals target.

## solution

Copied from: https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/discuss/1737839/Python-two-pointer-approach

```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        # The two pointers
        start = 0
        end = len(numbers) - 1

        # The loop will go on until the pointers collide
        while(start < end):
            # Defining the sum to be compared
            summ = numbers[start] + numbers[end]
            if(summ == target):
                return [start+1, end+1]
            # Former pointer incremented
            elif(summ < target):
                start += 1
            # Latter pointer decremented
            else:
                end -= 1
```
