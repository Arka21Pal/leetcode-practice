# [1382. Balance a Binary Search Tree](https://leetcode.com/problems/balance-a-binary-search-tree/)

> Given the `root` of a binary search tree, return *a* ***balanced*** *binary search tree with the same node values*. If there is more than one answer, return **any of them**.
>
> A binary search tree is **balanced** if the depth of the two subtrees of every node never differs by more than `1`.

First, we traverse each node of the tree with an "Inorder Traversal". Then, we recursively create root nodes for every sub-section of the tree (as the function is called recursively). Finally, we create sub-BSTs within the original BSTs in order to balance the BST.

## Solution

Copied from: https://leetcode.com/problems/balance-a-binary-search-tree/discuss/1922692/Python%3A-Clean-Recursive-Soln-or-Beats-60-soln-or-w-Comments-or-Time-and-Space-Complexity-O(n)

```python
class Solution:
    def inOrderTraversal(self, root):
        if not root:
            return

        # traverse left subtree
        self.inOrderTraversal(root.left)

        # append to list
        self.inOrderList.append(root)

        # traverse right subtree
        self.inOrderTraversal(root.right)

        return

    def createBBST(self,low, high):
        # base case
        if low > high:
            return None

        # pick middle node
        # Could also divide by 2, but this is fine
        mid = low + high >> 1

        # Recursively create nodes and the sub-BSTs
        node = self.inOrderList[mid]
        node.left = self.createBBST(low, mid - 1)
        node.right = self.createBBST(mid + 1, high)

        return node


    def balanceBST(self, root: TreeNode) -> TreeNode:
        self.inOrderList = []
        self.inOrderTraversal(root)
        return self.createBBST(0, len(self.inOrderList)-1)
```
