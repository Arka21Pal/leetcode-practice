# [110. Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/)

> Given a binary tree, determine if it is height-balanced.
>
> For this problem, a height-balanced binary tree is defined as:
>
> > a binary tree in which the left and right subtrees of *every* node differ in height by no more than 1.

In my opinion, this is actually a really tough problem. I have implemented the top-down approach for this, as I still do not understand the bottom-up approach.

The idea is this:

- We need to find the height of every node we get to whilst we iterate through the tree.
- Adjacent nodes should not have a difference in the heights of their respective subtrees of more than 1.
- Thus, we need to define a function which will, without exception, calculate the *entire* height from the node it is on, at that moment.
- With that, we will run another recursion with the main function, which will compare the total heights of each left and right node across the entire tree and check for unbalanced subtrees.

## Solution (top-down)

Time complexity: O(N^2) (do not understand the reason yet)
Shamelessly copied from: https://www.youtube.com/watch?v=OgdYyBT8iU8 (The first part of the video)

```python
"""
Top down approach
TC: O(N^2) as at each level we find the hieght of the levels below it
"""
class Solution:
    def isBalanced(self, root: Optional[TreeNode]) -> bool:

        # Define the function to calculate total height from any node that it is used on
        # This is done using an advantage that binary trees present to us
        # That is, if we iterate over the last node, we get "Null" as a result
        # Thus, we know where to stop iterating
        def height(node):

            # This is the very important step which will stop the iteration
            if node == None: return 0

            # The only way to return a number by incrementally adding values is this
            # To add a number in the final return statement
            # Here, this function will recursively run to find out the total hieght from any node it is run
            # And will stop when the condition above is met
            # Thus, it will output the total value of the height by adding 1s and a 0 at the end
            return 1 + max(height(node.left), height(node.right))

        # Of course, if the tree does not exist, it is a balanced tree
        if root == None: return True

        # The condition of the problem is that the difference in height should not be more than 1
        # Simply find out the difference in height between the left and right nodes
        if abs(height(root.left) - height(root.right)) > 1: return False

        # Remember that the step above only works because we recursively call the main function here
        # By calling it for the left and right nodes, we make sure that the difference between every node in the subtree is calculated
        return self.isBalanced(root.left) and self.isBalanced(root.right)
```
