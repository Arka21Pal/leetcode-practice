# This note contains the solutions to binary tree traversal problems

There are three main types of binary tree traversal problems:
- [94. Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)
- [144. Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/)
- [145. Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/)

I will cover all of them here, as the solutions (one-liners) are very similar to each other.

## Inorder Traversal

```python
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
            return self.inorderTraversal(root.left) + [root.val] + self.inorderTraversal(root.right) if root else []
```

## Preorder Traversal

```python
class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        return [root.val] + self.preorderTraversal(root.left) + self.preorderTraversal(root.right) if root else []
```

## Postorder Traversal

```python
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        return self.postorderTraversal(root.left) + self.postorderTraversal(root.right) + [root.val] if root else []
```

## Resources

- https://www.youtube.com/watch?v=WZwNoTm_9d8
- https://www.youtube.com/watch?v=Gi38tyDXn50
