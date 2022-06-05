# [230. Kth Smallest Element in a BST](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)

<blockquote>
Given the <code>root</code> of a binary search tree, and an integer <code>k</code>, return <i>the</i> <code>k<sup>th</sup></code> <i>smallest value</i> (<b>1-indexed</b>) <i>of all the values of the nodes in the tree</i>.
</blockquote>

Super simple, just in-order traversal into array and sort.

## Solution

```python
class Solution:
    def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:

        # Array
        s = []

        # In-order traversal
        def in_order(node):
            if node: s.append(node.val)
            if node.right: in_order(node.right)
            if node.left: in_order(node.left)
        in_order(root)

        # Sort and return element
        s.sort()
        return s[k-1]
```
