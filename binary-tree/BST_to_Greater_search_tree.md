# [1038. Binary Search Tree to Greater Sum Tree](https://leetcode.com/problems/binary-search-tree-to-greater-sum-tree/)

> Given the `root` of a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus the sum of all keys greater than the original key in BST.

Even though it's a medium level question, the solution is quite easy. I think with some practice I might even be able to solve such questions myself.

The idea is simple: we simply have to add the value of every node below the current node, which is greater in value than the current node. Which means that we need to traverse the sub-tree below each node, and add the respective values. The trick is to traverse the whole sub-tree and not just the `right` sub-tree. This is accomplished in two lines in the solution.

## Solution

Copied from: https://leetcode.com/problems/binary-search-tree-to-greater-sum-tree/discuss/1473284/python3-O(N)

```python
class Solution:
    def bstToGst(self, root: TreeNode) -> TreeNode:

        # Edge case: if tree doesn't exist, return 0 (the value of a non-existent tree)
        if not root:
            return 0

        # Random recursive function name
        def crippling_addiction(node, total):

            # If we've reached the end of the tree, return the last value of total (the sum of respective nodes)
            if not node: return total

            # If the node exists, add the value of a greater node to that
            # A greater node is always to the right in a BST
            if node: node.val += crippling_addiction(node.right, total)

            # But we need to traverse the entire sub-tree and not just the right sub-tree
            # Thus, after every iteration, move to the left sub-node and go from there
            return crippling_addiction(node.left, node.val)

        # Start from the root
        crippling_addiction(root, 0)

        # Return the now modified root
        return root
```
