# [563. Binary Tree Tilt](https://leetcode.com/problems/binary-tree-tilt/)

> Given the `root` of a binary tree, return the sum of every tree node's ***tilt***.
>
> The **tilt** of a tree node is the **absolute difference** between the sum of all left subtree node **values** and all right subtree node **values**. If a node does not have a left child, then the sum of the left subtree node **values** is treated as `0`. The rule is similar if the node does not have a right child.

## Solution

Copied from: https://leetcode.com/problems/binary-tree-tilt/discuss/1733957/Faster-than-94.88-of-python3

```python
class Solution:
    def findTilt(self, root: Optional[TreeNode]) -> int:
        # Declare variable to keep track of the total tilt
        self.i=0
        def inorder(node):
            if node is None:
                return 0
            # When the function reaches a leaf node
            if node.left is None and node.right is None:
                return node.val
            else:
                # Recursively traverse the entire tree
                l=inorder(node.left)
                r=inorder(node.right)
                self.i+=abs(l-r)
                return l+r+node.val
        inorder(root)
        return self.i
```
