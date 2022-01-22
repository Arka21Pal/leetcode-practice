# [Reshape the matrix](https://leetcode.com/problems/reshape-the-matrix/)

> You are given an `m x n` matrix `mat` and two integers `r` and `c` representing the number of rows and the number of columns of the wanted reshaped matrix.
>
> The reshaped matrix should be filled with all the elements of the original matrix in the same row-traversing order as they were.
>
> If the `reshape` operation with given parameters is possible and legal, output the new reshaped matrix; Otherwise, output the original matrix.

None of the following are my solutions, but they're decent.

## Solution 1

Link: https://leetcode.com/problems/reshape-the-matrix/discuss/1706338/Python-O(MxN)-solution-without-doing-math

```python
class Solution:
    def matrixReshape(self, mat: List[List[int]], r: int, c: int) -> List[List[int]]:

        # Check if the multiplication of lengths match (area in 2d)
        if r*c != len(mat)*len(mat[0]):
            return mat

        # Declare an empty stack to append elements to
        # This list will be returned, it will have multiple lists inside corresponding to each block of the new matrix
        output = []

        # Double loop to iterate through every element in every sub-list in the given list (matrix)
        for row in mat:
            for num in row:
                # If the last list in "output" (empty list defined before) doesn't match the required width
                # Append another empty list into output
                # This is because even though the width of the matrix might not match, this is a valid scenario (otherwise we wouldn't have come this far)
                if not output or len(output[-1]) == c:
                    output.append([])
                # And if it does indeed fit, append it to the last list of output
                output[-1].append(num)

        return output
```

## Solution 2

Link: https://leetcode.com/problems/reshape-the-matrix/discuss/1695659/Python3-Solutionor-Easy-to-understand-or-With-proper-comments

```python
class Solution:
    def matrixReshape(self, mat: List[List[int]], r: int, c: int) -> List[List[int]]:


        # ORIGINAL COMMENTS
        # first..to check if the reshape is valid, we compare
        # the product of #rows * #col in the given matrix and the asked matrix. both products should be equal to be valid

        # MY COMMENTS
        # Indeed, in order to check the validity of the structure of the new matrix, we multiply the rows and columns of the existing matrix, and then compare them to the value we get from multiplying "r" and "c", which are the length and the breadth of the new matrix

        # no of rows in given matrix
        M_row = len(mat)
        M_col = len(mat[0])

        # r and c are the expected #row and #col after reshape

        # to be valid, M_row * M_col == r * c, else return the original matrix
        if M_row * M_col != r*c:
            return mat

        # now reshape
        # first create an empty array of the asked shape (r X c)
        arr = [[None for j in range(c)] for i in range(r)]

        # ORIGINAL COMMENTS
        # linear array to store values from original matrix
        # so that it can be accessed sequentially

        # MY COMMENTS
        # This is so brilliant. The sequential read from this list will speed up the entire process by a sizeable margin

        dummy = []

        # adding data to dummy from original matrix
        for i in range(M_row):
            for j in range(M_col):
                dummy.append(mat[i][j])

        # index to traverse elements of dummy
        ind = 0

        # storing data in reshaped array 'arr'
        for i in range(r):
            for j in range(c):
                arr[i][j] = dummy[ind]
                ind+=1
        # The step above is very important
        # Since dummy is a sequential list, and we require an array of lists (for a 2d matrix)
        # We need to put the sequential elements into lists the size of the width of the new matrix
        # This will only work if the previous check of "if M_row * M_col != r*c" is passed

        return arr
```

## Solution 3

Link: https://leetcode.com/problems/reshape-the-matrix/discuss/1627747/Very-straightforward-Python-solution-86th-percentile-runtime

```python
class Solution:
    def matrixReshape(self, mat, r, c):
        m, n = len(mat), len(mat[0])

        # Check for validity of reshape
        if (m * n != r * c) or (m == r and n == c):
            return mat

        # Create output matrix
        out = []

        # Flatten the matrix
        M_flat = []
        for row in mat:
            M_flat += row

        # Populate rows with c elements taken sequentially from the flattened matrix, then add the row to the output matrix
        # Once complete the output matrix will have r rows consisting of c elements with the same row-traversing order as mat, as was desired
        while len(M_flat) > 0:
            row = []
            for i in range(c):
                x = M_flat.pop(0)
                row.append(x)
            out.append(row)

        return out
```
