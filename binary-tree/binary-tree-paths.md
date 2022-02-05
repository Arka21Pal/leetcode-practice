# [257. Binary Tree Paths](https://leetcode.com/problems/binary-tree-paths)

> Given the `root` of a binary tree, return *all root to leaf paths in* ***any order***.
>
> A **leaf** is a node without children.

Really simple problem. The idea is easy enough: iterate through the tree, and push all of the values you iterate through, into a string.\
Then, append the string to a list/stack, and return the stack.

## Solution

Copied from: https://leetcode.com/problems/binary-tree-paths/discuss/1712514/Simple-python-recursive-solution(For-beginners)

```python
class Solution:
    def binaryTreePaths(self, root: Optional[TreeNode]) -> List[str]:

        # Define an empty stack
        answers = []

        # Function to recursively call
        def repeat(node, s):

            # If the node does not exist, just stop
            if not node: return

            # If the loop is in the middle of an ongoing recursion
            # The value of "s" will be greater than 0
            # Which means we need to add the characters according to the demands of the question
            if len(s) > 0:
                s += "->" + str(node.val)
            # But if the function has been called for the first time, s will be empty
            else:
                s = str(node.val)

            # If there is no next node, we have reached the end of the tree
            # Append "s" to "answers"
            if not node.left and not node.right: answers.append(s)

            # Make sure to iterate through every element on the left and right
            repeat(node.left, s)
            repeat(node.right, s)

        # Call the function
        # It will append to "answers"
        repeat(root, "")

        # Return the finished list
        return answers
```
