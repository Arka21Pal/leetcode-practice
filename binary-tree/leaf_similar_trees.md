# [872. Leaf-Similar Trees](https://leetcode.com/problems/leaf-similar-trees/)

> Consider all the leaves of a binary tree, from left to right order, the values of those leaves form a **leaf value sequence**.

The idea is simple: put every possible "last" value (all of the possible endings of the tree) in a list. And compare.

## Solution

Copied from: https://leetcode.com/problems/leaf-similar-trees/discuss/1815341/Easy-Clean-Python-Solution

```python
class Solution:
    def leafSimilar(self, root1: Optional[TreeNode], root2: Optional[TreeNode]) -> bool:

        # Recursive function
        def dfs(root):

            # If not root, return nothing in the list
            if not root:
                return []

            # If at the end of tree, add the value of the node there
            if not root.left and not root.right:
                return [root.val]

            # Return the sum of the recursive function for both the left and right nodes so the correct values can be added to the list
            return dfs(root.left)+dfs(root.right)

        # Check if the two lists are the same, which is the condition for the problem
        return dfs(root1)==dfs(root2)
```
