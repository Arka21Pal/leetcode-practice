# [783. Minimum Distance Between BST Nodes](https://leetcode.com/problems/minimum-distance-between-bst-nodes/)

> Given the `root` of a Binary Search Tree (BST), return *the minimum difference between the values of any two different nodes in the tree*.

Simply have to calculate the minimum of two nodes in the tree. There's a few ways of doing that; I used a stack, the other answer just used a variable. The second solution is a lot more efficient than mine.

## My solution

```python
class Solution:
    def minDiffInBST(self, root: Optional[TreeNode]) -> int:

        # Empty stack
        stack = []
        # Maximum possible difference as the maximum value of a node is 10000
        diff = 100000

        # Recursive function
        def recurse(node):
            if node:
                # If node exists, append to the stack and keep going forward
                stack.append(node.val)
                recurse(node.left)
                recurse(node.right)

        # Start from the root
        recurse(root)

        # The logic to find the smallest difference
        # Keep modifying the value of "diff" till it matches the smallest difference
        stack.sort()
        for i in range(len(stack)-1):
            if diff > (stack[i+1] - stack[i]):
                diff = stack[i+1] - stack[i]

        # Return "diff"
        return diff
```

## Another solution

Link: https://leetcode.com/problems/minimum-distance-between-bst-nodes/discuss/1851528/Inorder-iterative-python

```python
class Solution:
    def minDiffInBST(self, root: Optional[TreeNode]) -> int:

        # Declarations
        stack = []
        ans = float('inf')
        pre = -float('inf')
        node = root

        # While stack or node exists
        while stack or node:
            while node:

                # Put the value of the node and everything to its left in the stack
                # On the first glance, this doesn't cover the entire tree, but the last command in this loop will make it work
                stack.append(node)
                node = node.left

            # Node takes the last value in the stack, i.e. the least (and last) value in the specific path of the tree
            node = stack.pop()

            # These two lines are basically subtracting the value of the current node from the previous node
            # Like in my solution, the variable "and" keeps the least value
            ans = min(ans, node.val - pre)
            pre = node.val

            # And then, we switch to the node on the right, this complements the inner while loop and completes the traversal of the tree
            node = node.right

        return ans
```
