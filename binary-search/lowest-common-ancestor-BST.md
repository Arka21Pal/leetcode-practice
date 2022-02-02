# [235. Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)

> Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.

The idea is simple:\
Given the values of two nodes, iterate through the tree. At every step, match the value of the current node to the maximum and minimum of the two provided nodes.\
If `current_node.val < max(node1.val, node2.val)` and `current_node.val < min(node1.val, node2.val)`, the next node will be the node on the left. If both conditions are reversed, then the next node is the node on the right.\
This is because the common node will have a value between the two given nodes. And the first node which has that is the first common ancestor. This is made easier by the tree being a binary search tree.

## Solution (recursive)

Copied from: https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/discuss/1737930/Python-EZPZ-Recursive-Faster-than-94

```python
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        # If either node does not exist, return None
        if p is None or q is None:
            return None

        # The minimum and maximum values of both elements
        # Technically, if we knew which element was to the left of the other element, we wouldn't have to do this
        left = min(p.val, q.val)
        right = max(p.val, q.val)

        # The function which will be recursively called
        def dfs(node, left, right):
            # If we reach the end of the tree without any matches
            if node is None:
                return None
            # If the value of the node is greater than both left and right, shift left to a lesser value
            if node.val > left and node.val > right:
                return dfs(node.left, left, right)
            # If the value of the node is lesser than both left and right, shift right to a greater value
            if node.val < left and node.val < right:
                return dfs(node.right, left, right)
            # Return the node for the recursion to work
            return node

        return dfs(root, left, right)
```

The concept is the same, even for iterative solutions

- https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/discuss/1729293/Python-Easy-To-Understand
- https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/discuss/1723966/Simple-Python-Solution-(Iterative-%2B-Recursive)%3A
- Video Guide: [Lowest Common Ancestor Binary Search Tree](https://www.youtube.com/watch?v=TIoCCStdiFo)
