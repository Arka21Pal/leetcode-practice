# [965. Univalued Binary Tree](https://leetcode.com/problems/univalued-binary-tree/)

> A binary tree is *uni-valued* if every node in the tree has the same value.
>
> Given the `root` of a binary tree, return `true` *if the given tree is* ***uni-valued***, *or* `false` *otherwise*.

Very simple, simply store the value of the root and compare the value of every subsequent node with it. That's all.

## Solution (`dfs`)

Copied from: https://leetcode.com/problems/univalued-binary-tree/discuss/1814363/Simple-dfs-solution

```python
class Solution:
    def isUnivalTree(self, root: Optional[TreeNode]) -> bool:

        # Value of root node
        value = root.val

        # Recursive function to compare values of the subsequent nodes to the root node
        def recurse(node):

            # If we've reached the end of the tree, all nodes match
            if not node:
                return True

            # If the value doesn't match, return False
            if node.val != value:
                return False

            # Return an "and" of the left and right nodes so that we get a consistent answer (what if one node doesn't match?)
            return recurse(node.right) and recurse(node.left)

        # Finally, return the recursive function to get the internal return values as expected output
        return recurse(root)
```

## Solution 2

Copied from a random solution, but I had the right idea.

```python
class Solution:
    def isUnivalTree(self, root: Optional[TreeNode]) -> bool:

        # When using a while loop to traverse a binary tree, always use a stack of some sort
        stack = collections.deque([root])

        # The required value
        value = root.val

        while stack:

            # Get the most recent value from the stack
            node = stack.popleft()

            # If the value doesn't match, stop immediately
            if node.val != value: return False

            # Append both left and right nodes to the stack to keep the traversal going
            if node.left: stack.append(node.left)
            if node.right: stack.append(node.right)

        # Assuming the loop finished without a problem, the binary tree is univalued
        return True
```
