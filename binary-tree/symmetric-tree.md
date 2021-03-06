# [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)

> Given the `root` of a binary tree, *check whether it is a mirror of itself* (i.e., symmetric around its centre).

The basic idea here is to compare the right side of the left node with the left side of the right node, and vice versa.

## My solution

Link: https://leetcode.com/submissions/detail/639723160/

I was revising this problem, and came up with a fast and easy solution. The logic is the same as above.

Stats:
> Runtime: 28 ms, faster than 97.61% of Python3 online submissions for Symmetric Tree.
> Memory Usage: 14 MB, less than 91.25% of Python3 online submissions for Symmetric Tree.

```python
class Solution:
    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        def recurse(node1, node2):

            # If both nodes don't exist, we have reached the end of both subtrees
            if not node1 and not node2: return True

            # If either node doesn't exist, obviously it is asymmetrical
            if not node1 or not node2:  return False

            # If the value of one node is not equal to the value of the other node, the tree is asymmetrical
            if node1.val != node2.val:  return False

            # Recursively get both the left and right subtrees for comparison
            left = recurse(node1.left, node2.right)
            right = recurse(node1.right, node2.left)

            # Only if the two subtrees are symmetrical, will this function return True
            return left and right

        # Start the function from the left and right subtrees, from the root
        return recurse(root.left, root.right)
```

## My proposed solution

Shamelessly copied from: https://leetcode.com/problems/symmetric-tree/discuss/1693514/how-recursion-solves-this-problem..

```python
class Solution:
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

            # If a node on one side doesn't exist or their values don't match, return False
            if node1 == None or node2 == None or node1.val != node2.val:
                return False

            # Otherwise, append to the stack again, this time for both right and left of both nodes
            stack.append((node1.left, node2.right))
            stack.append((node1.right, node2.left))

        return True
```
