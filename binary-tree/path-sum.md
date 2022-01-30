# [112. Path Sum](https://leetcode.com/problems/path-sum/)

> Given the `root` of a binary tree and an integer `targetSum`, return `true` if the tree has a *root-to-leaf* path such that adding up all the values along the path equals `targetSum`.

> A *leaf* is a node with no children.

The easiest approach to this would be recursion.

## Solution 1

Copied from: https://leetcode.com/problems/path-sum/discuss/1696898/Python-or-Recursive-or-Easy-to-read

```python
class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root:
            return False

        def hasMatchingSum(node, total):
            # Return False if the tree doesn't exist
            if node is None:
                return False

            # Tracking the total
            total += node.val

            # Check if the targetSum is achieved by the end of the tree
            if node.left is None and node.right is None:
                return total == targetSum

            # Call the function recursively to calculate for both sides of every node
            leftMatch = hasMatchingSum(node.left, total)
            rightMatch = hasMatchingSum(node.right, total)

            # Assuming either one, or both get it right
            return leftMatch or rightMatch

        return hasMatchingSum(root, 0)
```

## Solution 2

An iterative, `DFS` solution.

Link: https://leetcode.com/problems/path-sum/discuss/1661687/Python-or-Iterative-DFS-using-Deque

```python
class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root:
            return False
        # "dequeue" instead of list
        st = collections.deque()
        # Append both the starter node and the remaining value
        st.append((root, targetSum-root.val))
        while st:
            # Pop it every time so that "st" remains clean
            n, v = st.pop()
            # If there's no node left at the end
            # And the targetSum has been acheived, return True
            if not n.left and not n.right and v == 0:
                return True
            # If left node exists, append that and the remaining value
            if n.left:
                st.append((n.left, v-n.left.val))
            # If right node exists, append that and the remaining value
            if n.right:
                st.append((n.right, v-n.right.val))
        return False
```
