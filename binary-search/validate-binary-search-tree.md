# [98. Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)

> Given the `root` of a binary tree, *determine if it is a valid binary search tree (BST)*.

The logic is simple: compare all the values of the "left" nodes to the "right" nodes, and if the left node has a greater value that the right node, this is not a proper BST.

## Solution

Shamelessly copied from: https://leetcode.com/problems/validate-binary-search-tree/discuss/1730627/Python-inorder-traversal-iteration-99.67-faster-99.68-less-memory

```python
class Solution:
    def isValidBST(self, root: Optional[TreeNode]) -> bool:

        # The original solution used a plain list, but using this shaves off a few microseconds
        queue = collections.deque()
        # Just another variable to use as a dummy in the loop
        pre = None

        # To keep the loop running after the pointer reaches the end of the tree
        while queue or root:
            # Fill up the queue to use in the next step
            while root:
                queue.append(root)
                root = root.left
            # Go from last node to first node of tree, to compare later on
            root = queue.pop()
            # The first time the loop runs, this will be useless
            # But in time, "pre" will have the last value of "root"
            # And because we're now taking the value of the nodes on the right ("root = root.right")
            # It can compare the values of the nodes on the right with those on the left
            if pre and pre.val >= root.val:
                return False
            pre = root
            root = root.right
        # Of course, if it's a real tree, return True
        return True
```

There's another, similar solution (albeit, using recursion) here: https://leetcode.com/problems/validate-binary-search-tree/discuss/1708937/The-most-pythonic-clean-solution
