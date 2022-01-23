# [Valid Sudoku](https://leetcode.com/problems/valid-sudoku/)

## Copied solution

This is a brilliant, snarky solution.

Link: https://leetcode.com/problems/valid-sudoku/discuss/1709467/Python-using-numpy-and-set

```Python
# Import numpy
import numpy as np

class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:

        # Load the board into numpy
        arr = np.array(board)

        # Quite literally check all of the rows and columns together
        # First, replace those pesky fullstops
        # The "[i,:]" signifies rows
        # And the "[:,i]" signifies columns
        # Finally, check for any common elements with "set()"
        # Remember that "set()" will remove all duplicate elements (thus producing the shortest list/array)
        # Thus, if the length of the shortened array and the original array match, the elements haven't been repeated

        for i in range(9):
            r = "".join(arr[i,:]).replace(".","")
            c = "".join(arr[:,i]).replace(".","")
            if len(r) > len(set(r)) or len(c) > len(set(c)):
                return False

        # This is the same logic as before, but for 3x3 boxes inside the big sudoku maze
        # Basically, by using counts of 3 {in "range(0,9,3)"}, he only takes a single 3x3 box at a time
        # Then, uses "set()" again, as all the fullstops have already been substituted in the previous step

        for i in range(0,9,3):
            for j in range(0,9,3):
                box = "".join(arr[i:i+3,j:j+3].flatten()).replace(".","")
                if len(box) > len(set(box)):
                    return False

        return True
```

*Question*: Why does he `flatten` the box in this step?

> `box = "".join(arr[i:i+3,j:j+3].flatten()).replace(".","")`
