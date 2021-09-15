# Remove Duplicates from Sorted Array

Looks fairly simple at first. Keep only the unique elements at the beginning of the array, with their order being the same as in the original array, and return the number of the first bunch of unique elements in the array.

> Given an integer array `nums` sorted in **non-decreasing order**, remove the duplicates [in-place](https://en.wikipedia.org/wiki/In-place_algorithm) such that each unique element appears only **once**. The **relative order** of the elements should be kept the **same**.

## My solution

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        if len(nums) < 2: # No need to do anything if number of elements is less than two
            return len(nums)
        k = 1
        for i in range(1, len(nums)):
            if nums[i-1] != nums[i]: # i.e. if it's an unique element
                nums[k] = nums[i] # change postion of element to get the unique elements to the beginning of the array.
                k = k + 1 # Update the variable to be returned when this happens
        return k
```

## [98.76% faster, Python, O(1), Beginner Friendly with comments](https://leetcode.com/problems/remove-duplicates-from-sorted-array/discuss/1364660/98.76-faster-Python-O(1)-Beginner-Friendly-with-comments)

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        index = 1
        for i in range(1,len(nums)):
            if(nums[i-1]!=nums[i]):
                nums[index] = nums[i]
                index+=1
        return index
```

## [[Python/Python3] Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/discuss/1235769/PythonPython3-Remove-Duplicates-from-Sorted-Array)

An arguably better solution for it uses the concept of double pointers, which I still can't a grasp on.

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        
        if not nums:
            return 0
        
        unik_pointer = 0
        idx_pointer = 0
        
        while idx_pointer < len(nums)-1:
            if nums[idx_pointer] != nums[idx_pointer+1]:
                nums[unik_pointer+1] = nums[idx_pointer+1]
                unik_pointer += 1
            # else:
            idx_pointer += 1
        
        return unik_pointer+1
```

## [Easy to understand :Python Time O(n), Space O(1)](https://leetcode.com/problems/remove-duplicates-from-sorted-array/discuss/1274088/Easy-to-understand-%3APython-Time-O(n)-Space-O(1))

```python
    n = len(nums)
    ##Corner case:Array has 0 or 1 element
    if(n==0 or n==1):
        return n

    j=1
    for i in range(1,n):
        if(nums[i]!=nums[i-1]):
            nums[j]=nums[i]
            j+=1
    return j
```

*A lot of the solutions work by swapping elements, but the double pointer approach is interesting*
