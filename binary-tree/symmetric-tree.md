# [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)

> Given the `root` of a binary tree, *check whether it is a mirror of itself* (i.e., symmetric around its centre).


Unfortunately, nothing that I've tried is working. It exits with this error:
```
NameError: name 'Solution' is not defined
    ret = Solution().isSymmetric(param_1)
    Line 55 in _driver (Solution.py)
        _driver()
        Line 66 in <module> (Solution.py)
```

The basic idea here is to compare the right side of the left node with the left side of the right node, and vice versa.

## My proposed solution

Shamelessly copied from: https://leetcode.com/problems/symmetric-tree/discuss/1693514/how-recursion-solves-this-problem..

```python
def isSymmetric(self, root: Optional[TreeNode]) -> bool:

    # Return True if root is none, because a non-existent tree is considered symmetrical
    if root == None: return True

    # Function for recursion
    def repeat(right,left):
        # If right and left don't exist, i.e. if the right and left node from root (and so on), do not exist
        if right is None and left is None:
            return True
        # If however, they do exist, and their values match
        # Go through the function once again, this time with the next values of both right and left
        if right and left and right.val == left.val:
            return repeat(right.right,left.left) and repeat(right.left,left.right)
        # If that doesn't work, return False
        else: return False

    return repeat(root.right,root.left)
```

## Another solution using "iteration"

Link: https://leetcode.com/problems/symmetric-tree/discuss/1686507/Recursive-and-iterative-solutions-in-Python

```python
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:

        # Using a stack to compare values
        stack = [(root.left, root.right)] if root != None else []

        # Checking length of stack to ensure that elements exist
        while len(stack) > 0:

            # Pop the values from the stack to compare
            node1, node2 = stack.pop()

            # If nodes don't exist, carry on
            if node1 == None and node2 == None:
                continue

            # If either node doesn't exist or their values don't match, return False
            if node1 == None or node2 == None or node1.val != node2.val:
                return False

            # Otherwise, append to the stack again, this time for both right and left of both nodes
            stack.append((node1.left, node2.right))
            stack.append((node1.right, node2.left))

        return True
```
