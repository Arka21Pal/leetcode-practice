# [993. Cousins in Binary Tree](https://leetcode.com/problems/cousins-in-binary-tree/)

> Given the `root` of a binary tree with unique values and the values of two different nodes of the tree `x` and `y`, return `true` *if the nodes corresponding to the values* `x` *and* `y` *in the tree are* ***cousins***, *or* `false` *otherwise*.
>
> Two nodes of a binary tree are **cousins** if they have the same depth with different parents.

The thing is, the question really tells you what to do. It's just the problem of how to implement it. The idea is this: whilst traversing the tree, treat each node as the parent (assuming it is not the last node). Thus, every next node subsequently becomes the child. Then, check if the depths of the child nodes are equal, and if the parents have different values. IF these conditions match, return true.

## Solution

Copied from: https://leetcode.com/problems/cousins-in-binary-tree/discuss/1900052/Python-DFS

```python
class Solution:
    def isCousins(self, root: Optional[TreeNode], x: int, y: int) -> bool:

        # It is important to declare variables with the "self" prefix as we're going to be using them in a different function under the same class
        # This is acting like an __init__ function for these variables
        self.x = x
        self.y = y
        self.xdepth = 0
        self.ydepth = 0
        self.xparent = 0
        self.yparent = 0

        # Calling the function we define later
        self.recursive_find(root, 0, root.val)

        # The conditions mentioned in the explanation
        # 1. The values of the parents should not be equal to each other
        # 2. The depths of the children should be equal
        if self.xparent != self.yparent and self.xdepth == self.ydepth:
            return True
        else: return False

    def recursive_find(self, node, depth, parent):

        # If node doesn't exist, leave
        if not node: return 0

        # If the value of the current node is equal to the value of x, define depth and parent for this node
        if node.val == self.x:
            self.xdepth = depth
            self.xparent = parent

        # If the value of the current node is equal to the value of y, define depth and parent for this node
        if node.val == self.y:
            self.ydepth = depth
            self.yparent = parent

        # Traverse the entire tree by going through left and right nodes
        # Also increment the depth of the nodes, and define the parent as the current node value as the function moves forward
        self.recursive_find(node.left, depth+1, node.val)
        self.recursive_find(node.right, depth+1, node.val)
```
