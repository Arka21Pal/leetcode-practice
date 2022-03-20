# [1379. Find a Corresponding Node of a Binary Tree in a Clone of That Tree](https://leetcode.com/problems/find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree/)

> The `cloned` tree is a **copy of** the `original` tree.
>
> Return *a reference to the same node* in the `cloned` tree.

The idea is, again, very simple: go through both trees, and if at any point, the node of `original` matches the `target`, return the node of `cloned`.

## Solution

Copied from: https://leetcode.com/problems/find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree/discuss/1829968/Python-DFS

```python
class Solution:
    def getTargetCopy(self, original: TreeNode, cloned: TreeNode, target: TreeNode) -> TreeNode:

        # Recursive function to check if node(s) exist
        def recurse(node1, node2, target):
            if not node1 or not node2: return

            # The main logic of this snippet: if node of the first tree matches target, return node of tree 2
            if node1 == target:
                return node2

            # This is also very important
            # Iterate through the trees by giving the left and right nodes of the current nodes as input to the recursive function
            return recurse(node1.left, node2.left, target) or recurse(node1.right, node2.right, target)

        # Do not forget the return, and start from the beginning for both trees
        return recurse(original, cloned, target)
```
