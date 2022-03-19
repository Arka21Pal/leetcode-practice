# [1302. Deepest Leaves Sum](https://leetcode.com/problems/deepest-leaves-sum/)

> Given the `root` of a binary tree, return *the sum of values of its deepest leaves*.

The idea is fairly simple: record the level of every element in the tree, as you traverse through it. Add the elements at the last level, and return it. The dictionary maintains elements and levels for ease of access.

## Solution

Copied from: https://leetcode.com/problems/deepest-leaves-sum/discuss/1818875/90-faster-and-98-less-in-memory-DFS-using-python

```python
class Solution:
    def deepestLeavesSum(self, root: Optional[TreeNode]) -> int:

        # The dictionary I use to record levels and the sum of elements
        levels = {}

        # Recursive function to iterate through the tree
        def recurse(node, count):

            # If node doesn't exist, we've reached the end of the tree. It's time to stop at this point
            if not node:
                return 0

            # If this is the last node in a certain path
            if not node.left and not node.right:

                # Check if the level is already recorded in the dictionary
                if count in levels:
                    levels[count] += node.val
                else:
                    # If not, start a new record with that particular level
                    levels[count] = node.val

            # Recursively go through every possible node and record their levels and sum
            recurse(node.left, count+1)
            recurse(node.right, count+1)

        # Start from root and level 0
        recurse(root, 0)

        # Return the sum of the elements from the last level of the tree
        return levels[max(levels.keys())]
```

