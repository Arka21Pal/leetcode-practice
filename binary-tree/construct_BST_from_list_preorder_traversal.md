# [1008. Construct Binary Search Tree from Preorder Traversal](https://leetcode.com/problems/construct-binary-search-tree-from-preorder-traversal/)

> Given an array of integers preorder, which represents the **preorder traversal** of a BST (i.e., **binary search tree**), construct the tree and return *its root*.
>
> A **binary search tree** is a binary tree where for every node, any descendant of `Node.left` has a value **strictly less than** `Node.val`, and any descendant of `Node.right` has a value **strictly greater than** `Node.val`.
>
> A **preorder traversal** of a binary tree displays the value of the node first, then traverses `Node.left`, then traverses `Node.right`.

The idea is simple: if the length of the provided list is greater than 0, then;
- The value of the next node is the first value of the processed list we get through our recursive function.
- The node to the left is the first element in the list having a value less than "value" which we define above.
- Similarly, the node to the right is the first element in the list with a value greater than "value".
- Finally, we return a `TreeNode(val = value, left = left, right = right)`.
- And then we call the recursive function.

## Solution

Copied from: https://leetcode.com/problems/construct-binary-search-tree-from-preorder-traversal/discuss/1970780/python-recursive-easy-to-read

```python
class Solution:
    def bstFromPreorder(self, preorder: List[int]) -> Optional[TreeNode]:

        # Recursive function
        def make_element(p):

            # If the length of the list is more than zero
            if len(p) > 0:
                # The first element will become the value for the TreeNode
                value = p[0]
                # The left node will be the first element with a value less than p[0]
                left = make_element([i for i in p[1:] if i < value])
                # The right node will be the first element with a value greater than p[0]
                right = make_element([i for i in p[1:] if i > value])
                # Return the TreeNode with parameters
                return TreeNode(val = value, left = left, right = right)
            else: return None

        return make_element(preorder)
```
