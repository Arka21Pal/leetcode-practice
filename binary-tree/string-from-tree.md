# [606. Construct String from Binary Tree](https://leetcode.com/problems/construct-string-from-binary-tree/)

> Given the `root` of a binary tree, construct a string consisting of parenthesis and integers from a binary tree with the preorder traversal way, and return it.
>
> Omit all the empty parenthesis pairs that do not affect the one-to-one mapping relationship between the string and the original binary tree.

The idea is very simple: use preorder traversal to get through the tree, and simply return it in the required format. If the right node does not exist, do not inset the round brackets for it. The round brackets for the left node (whether it exists or not) needs to be present.

## Solution

```python
class Solution:
    def tree2str(self, root: Optional[TreeNode]) -> str:
        # When we reach the end of the tree, or if the tree doesn't exist (any more)
        if root is None:
            return ""

        # If root is leafnode
        if root.left is None and root.right is None:
            return f'{root.val}'

        # If no right node, continue on the left without leaving "()" for the right
        if root.right is None:
            return f'{root.val}({self.tree2str(root.left)})'

        # Of course, if both nodes are present, simply call the function recursively
        return f'{root.val}({self.tree2str(root.left)})({self.tree2str(root.right)})'
```
