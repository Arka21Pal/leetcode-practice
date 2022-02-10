# [572. Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree/)

> Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` with the same structure and node values of `subRoot` and `false` otherwise.

The idea is very simple: because we're to check if the subtree is the same as the other tree, we simply compare the different nodes. The easiest way to do this is with recursion. Thus, the function inside the main function just checks the nodes with these conditions;
- If both `root` and `subRoot` don't exist, we have reached the end of the trees. The function is constructed in such a manner, that if we've reached this step, the trees are equal.
- If both `root` and `subRoot` exist, and if the value of the nodes are equal: recursively call the function to check the left and right nodes for both trees (thus, left and right sides of both nodes).
- If none of these conditions are triggered, consider the trees as unequal.

To actually return `True` from the main function, we need to return `True` from this function, and then recursively call the main function. Thus, if the interior function is `True`, return `True`. Which is why our final statement is an `or` between the left and right nodes of the main tree with the subtree.

## Solution

Copied from: https://leetcode.com/problems/subtree-of-another-tree/discuss/1741707/Python-3-or-Recursion-or-10-lines-or-Beats-85.9

```python
class Solution:
    def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
        # If either root or subRoot does not exist, the trees are obviously not equal
        if (not root or not subRoot) and (root!=subRoot):
            return False
        # If both exist, and their values match (because that's the only way both trees can be equal)
        if root and subRoot and root.val==subRoot.val:
            def check(root,subRoot):
                # If both do not exist, we have reached the end of the tree
                if root==subRoot==None:
                    return True
                # If both exist and their values match, check for the left and right nodes for both
                if root and subRoot and root.val==subRoot.val:
                    return check(root.left,subRoot.left) and check(root.right,subRoot.right)
                # If neither of these conditions are triggered, the trees are not equal
                return False
            # If the trees are equal, the function will return True
            # Return True in that case
            if check(root,subRoot): return True

        # Only if we return True in the previous case, can this step work
        # We're saying that if the subtree matches with the main tree on either side of root, return True
        return self.isSubtree(root.left,subRoot) or self.isSubtree(root.right,subRoot)
```

Similar solution: https://leetcode.com/problems/subtree-of-another-tree/discuss/1702724/check-if-same-tree
