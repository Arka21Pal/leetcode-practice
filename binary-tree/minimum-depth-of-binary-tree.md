# [111. Minimum Depth of Binary Tree](https://leetcode.com/problems/minimum-depth-of-binary-tree/)

> Given a binary tree, find its minimum depth.
>
> The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

Super easy problem, very similar in logic to the first part of the "balanced binary tree" problem (number 110).\
I'm not quite sure why I couldn't just copy-paste the logic between the two problems, but whatever.

## Solution

Copied from: https://leetcode.com/problems/minimum-depth-of-binary-tree/discuss/1742438/Python-solution-DFS-O(n)

```python
class Solution:
    def minDepth(self, root: Optional[TreeNode]) -> int:

        # Define a function to calculate minimum height
        def height(node, total):

            # Return "total - 1" for a leaf node, because we start from 1 (at the end of the solution)
            if not node: return total - 1

            # If "node.left"/"node.right" exists, change to that and add to total
            if node.left and not node.right: return height(node.left, total + 1)
            if node.right and not node.left: return height(node.right, total + 1)

            # Return the minimum of the heights between the two choices of left and right, if both sides exist
            return min(height(node.left, total + 1), height(node.right, total + 1))

        # Return the function, "total" starting from 1
        return height(root, 1)
```
