# [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)

> Given the `root` of a binary tree, return *the level order traversal of its nodes' values*. (i.e., from left to right, level by level).

The idea is this:
- The returned output will maintain level if we uniformly check the values of elements on both sides simultaneously.
- Thus, ever iteration will have to store the values of both "head.right" and "head.left", on multiple branches, together.

## Solution

Link: https://leetcode.com/problems/binary-tree-level-order-traversal/discuss/1722218/Implementation-using-queues-Beats-95-memory-use

```python
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        # Edge condition
        if not root: return []

        # Declaring lists
        queue, r_array = [root],[]

        # Iterating through the loop for elements at the same level
        while queue:
            # Empty list to be a draft for the final list
            r = []
            for _ in range(len(queue)):
                # Every element will be in order if immediately popped
                node = queue.pop(0)
                if node:
                    # Append the value of the most recent element
                    # Then append the values of the next elements in level to the queue
                    r.append(node.val)
                    queue.append(node.left)
                    queue.append(node.right)
            # Copy from draft list to final list
            if len(r) > 0: r_array.append(r)
        return r_array
```
