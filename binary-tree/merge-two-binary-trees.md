# [617. Merge Two Binary Trees](https://leetcode.com/problems/merge-two-binary-trees/)

> You are given two binary trees `root1` and `root2`.
>
> Imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not. You need to merge the two trees into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of the new tree.
>
> Return *the merged tree*.

Basically, just add the values of each respective node (left with left, right with right), and recursively call the function for the left and right nodes. Finally, return the tree of `root1`. If either node doesn't exist, return the one that does exist.

## Solution

Link: https://leetcode.com/problems/merge-two-binary-trees/discuss/1724430/Python-3-(120ms)-or-No-Extra-Space-Recursive-7-Lines-or-Easy-to-Understand

```python
class Solution:
    def mergeTrees(self, root1: Optional[TreeNode], root2: Optional[TreeNode]) -> Optional[TreeNode]:

        # If both nodes exist can we add the values
        if root1 and root2:
            root1.val  += root2.val

            # Recursively call the main function to find the sums for the left and right nodes
            root1.left = self.mergeTrees(root1.left, root2.left)
            root1.right = self.mergeTrees(root1.right, root2.right)

            # Return "root1" as we're adding the values to that
            return root1
        else:

            # Return the node that does exist
            return root1 or root2
```

Another solution which is basically the same thing, but with more conditions: https://leetcode.com/problems/merge-two-binary-trees/discuss/1763544/Python-Simple-Python-Solution-Using-DFS-With-the-help-of-Recursion
