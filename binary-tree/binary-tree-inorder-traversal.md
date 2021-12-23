# [Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)

> Given the `root` of a binary tree, return *the inorder traversal of its nodes' values*.

## My solution

A measly, unoriginal, but elegant one-liner.
Copied from: https://leetcode.com/problems/binary-tree-inorder-traversal/discuss/1613824/One-line-python-faster-than-99

```python
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
            return self.inorderTraversal(root.left) + [root.val] + self.inorderTraversal(root.right) if root else []
```

There are other solutions to this, but I haven't understood them yet. I'll record them when I understand wtf is going on.

## Resources

- https://www.youtube.com/watch?v=WZwNoTm_9d8
- https://www.youtube.com/watch?v=Gi38tyDXn50
