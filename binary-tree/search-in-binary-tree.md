# [700. Search in a Binary Search Tree](https://leetcode.com/problems/search-in-a-binary-search-tree/)

> You are given the `root` of a binary search tree (BST) and an integer `val`.
>
> Find the node in the BST that the node's value equals `val` and return the subtree rooted with that node. If such a node does not exist, return `null`.

Super easy problem, can solve using either iteration or recursion. It's basically the same thing done in two ways.

# Solution

Copied from: https://leetcode.com/problems/search-in-a-binary-search-tree/discuss/1715687/Python-Solution%3A-Recursive-and-Iterative-(faster-than-95)

- Recursion
    ```python
    class Solution:
    def searchBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:
        # If tree doesn't exist
        if root is None:
            return None
        # If we get lucky
        elif root.val == val:
            return root
        # If target value is less than root node value, search in the right side
        elif root.val < val:
            return self.searchBST(root.right, val)
        # If target value is more than root node value, search in the left side
        else:
            return self.searchBST(root.left, val)

        # It is a feature of binary search trees that the value on the left is always lesser than the value on the right node
    ```

- Iteration
    ```python
    class Solution:
    def searchBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:
        cur_node = root
        while cur_node:
            # If it matches
            if cur_node.val == val:
                return cur_node
            # If target val is lesser than current Node, then search on left side
            elif cur_node .val > val:
                cur_node = cur_node.left
            # If target val is more than current Node, then search on right side
            else:
                cur_node = cur_node.right
        return None
    ```
## Note

A shorter version of the solution can be found [here](https://leetcode.com/problems/search-in-a-binary-search-tree/discuss/1578911/Recursive-and-iterative-solution-in-Python)
