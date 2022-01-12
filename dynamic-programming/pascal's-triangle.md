# [Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/)

> Given an integer `numRows`, return the first `numRows` of Pascal's triangle.

I couldn't solve it, although I had the right idea for the brute-force solution. Fuck.

## Brute force

Link: https://leetcode.com/problems/pascals-triangle/discuss/1672115/From-Brute-force-to-DP

```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        # Define conditions to not get fucked in the edge cases
        if numRows == 1:
            return [[1]]
        if numRows == 2:
            return [[1], [1,1]]

        # Start the real problem
        output = [[1], [1,1]]
        while len(output)<numRows:

            # Start with 1
            # Append the addition of consecutive numbers to the list
            # When that's done, append another 1 to complete the list
            temp = [1]
            for i in range(len(output)-1):
                a = output[-1]
                temp.append(a[i]+a[i+1])
            temp.append(1)
            output.append(temp)
        return output
```

## Dynamic programming

A beautiful solution.\
Link: https://leetcode.com/problems/pascals-triangle/discuss/1672115/From-Brute-force-to-DP

```python
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        # Create a list of lists to access and append respectively
        pascal = [[1]*i for i in range(1, numRows+1)]
        for i in range(2, numRows):
            for j in range(1, i):
                # Access each individual list from the big list above
                # Add consecutive numbers from the previous list and append to the present list
                pascal[i][j] = pascal[i-1][j-1] + pascal[i-1][j]
        return pascal
```

Another link: https://leetcode.com/problems/pascals-triangle/discuss/1679769/Python-solution-explained
