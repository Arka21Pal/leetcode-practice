# [404. Sum of Left Leaves](https://leetcode.com/problems/sum-of-left-leaves/)

> Given the `root` of a binary tree, return the sum of all left leaves.

This is actually a very easy problem: Simply count the total of the left nodes of every node in the tree. I.e. even if you turn right, calculate the sum of the left nodes of that right node. That's all.

Obviously you'd need a `count` variable to hold the count. This time, I copied a solution using an `__init__` function (I've never done that before), which held the `count` variable.

## Solution

Copied from: https://leetcode.com/problems/sum-of-left-leaves/discuss/1686310/Sum-of-the-Left-Leaves-or-Python

```python
class Solution:
    # This is the "__init__" function which holds the variable to count
    def __init__(self):
        self.sum = 0
        
    def sumOfLeftLeaves(self, root):
		# Defined a function with two pointers
        def helper(root,node):
            if root:
                # If the left side of "node" exists
                if node.left != None:
                    if root.left is None and root.right is None and node.left == root:
                        self.sum += root.val
                left = helper(root.left,root)
                right = helper(root.right,root)
        
        
        helper(root,root)
        return self.sum
```
