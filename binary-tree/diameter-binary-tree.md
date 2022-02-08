# [543. Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)

> The **diameter** of a binary tree is the *length* of the longest path between any two nodes in a tree. This path may or may not pass through the `root`.

This is an easy problem: simply traverse the tree using `postorder` traversal, and calculate the total distance (in a variable). Instead of overcomplicating things with trying to actually find the distance between two nodes, just keep adding the maximum value of the distance of the node from the root. As we're doing this on both sides, the total distance between the last nodes will be when the recursion stops on both ends, and the variable will have the total distance between them.

And I don't know why it's called the diameter.

## Solution

Copied from: https://leetcode.com/problems/diameter-of-binary-tree/discuss/1742864/Python-resursive-DFS-with-comments

```python
class Solution:
    def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:

        # Variable to store the total distance (diameter)
        dia = 0

        # The recursive function
        def recursive(node):

            # Declaring it as non-local to use it in this function
            nonlocal dia

            # If the node doesn't exist, simply return 0, as that means that the function has reached the end of the tree
            if not node: # null case
                return 0

            # In order traversal to go through every left and right node
            left = recursive(node.left)
            right = recursive(node.right)

            # Get the maximum distance between nodes on either side
            dia = max(dia, left+right)

            # Because we need to increment the value of "dia", we will need to return 1+max(left, right)
            # This is to give "dia" the maximum value (because we don't know which side is longer)
            return 1 + max(left,right)

        # Go through the tree
        recursive(root)

        # Return the maximum distance
        return dia
```
