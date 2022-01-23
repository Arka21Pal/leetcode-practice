# [Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)

> Write an efficient algorithm that searches for a value in an `m x n` matrix. This matrix has the following properties:
> - Integers in each row are sorted from left to right.
> - The first integer of each row is greater than the last integer of the previous row.

Easy problem (even though it is labelled as "medium"), the simple idea is to search from the middle, and eliminate half of the remaining list depending on the condition.

That is, if the last element of a particular sub-list on one side of the matrix is greater than the target we want, eliminate the other half of the list, and use this side. And repeat. Until there's only a single sub-list left, and search inside that.

Of course, the brute-force method would be search every list, but what is the point in that?

These solutions aren't mine, although the idea used is the same.

## Solution 1

Link: https://leetcode.com/problems/search-a-2d-matrix/discuss/1712302/Python3-Binary-Search-or-faster-than-97

```python
class Solution:
    def searchMatrix(matrix, target):
        # print(matrix)

        # As this is an uniform matrix, it is easy to take its number of rows and columns from its sub-lists
        nRows = len(matrix)
        nCols = len(matrix[0])
        start = 0
        end = (nRows * nCols) - 1

        # This approach is interesting, because instead of considering the input as a list of lists, he considers it as a matrix
        # In this loop, he eliminates entire boxes (i.e. both rows and columns together) instead of just lists
        # Of course, this is just a way of seeing it, and doing it normally (eliminating lists) essentially does the same thing

        while start <= end:

            # Note that "start" is literally the first element of the first sublist, whilst "end" is the end of the matrix
            # That is, in terms of lists, the very last element

            mid = int((start + end)/2)

            # As we're considering a 2D matrix, these are the row and column in the middle
            # Of course, matrix[midRow][midCol] will point to a specific element

            midRow = int(mid/nCols)
            midCol = int(mid%nCols)

            # Checking for target
            if matrix[midRow][midCol] == target:
                print(f"found! at {midRow},{midCol} ")
                return True
            # Otherwise, "start" gets the old value of "mid"
            elif matrix[midRow][midCol] < target:
                start = mid + 1
            else:
                end = mid - 1
        return False
```

## Solution 2

This is not a binary search, but instead is the brute-force method

Link: https://leetcode.com/problems/search-a-2d-matrix/discuss/1698750/Python3-Runtime%3A-32-ms-faster-than-99.38-or-Memory%3A-14.7-MB-less-than-86.37

```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        rows = len(matrix)
        count = 0
        flag = 0
        while count < rows:
            last = matrix[count][-1]

            # Checking if the last element of the sub-lists are greater than or equal to target
            if last >= target:
                flag = 1
                break
            else:
                count += 1

        # If the element is found, stop
        if flag and target in matrix[count]:
            return True
        return False
```
