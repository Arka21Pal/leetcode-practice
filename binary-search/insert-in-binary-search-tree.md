# [701. Insert into a Binary Search Tree](https://leetcode.com/problems/insert-into-a-binary-search-tree/)

> You are given the `root` node of a binary search tree (BST) and a `value` to insert into the tree. Return *the root node of the BST after the insertion*. It is **guaranteed** that the new value does not exist in the original BST.
>
> **Notice** that there may exist multiple valid ways for the insertion, as long as the tree remains a BST after insertion. You can return **any of them**.

This is actually an easy problem, however all of my efforts to solve it were incorrect. I even tried to write similar to the answers, still nothing. I've resigned myself to copying the solution I liked, although it's not very efficient.

# Solution

Copied from: https://leetcode.com/problems/insert-into-a-binary-search-tree/discuss/1698646/both-recursive-and-iterative-solution..

- Iterative
    ```python
    class Solution:
        def insertIntoBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:

            # If the tree doesn't exist, return the given "val" as a node (rather, the node)
            if root == None:
                return TreeNode(val)

            # Required variables for this approach
            # Here, we consider that "node" will be iterating over the tree
            # And "parent" is the element where "node" stops
            # Basically, the new node will be after "parent"
            parent = None
            node = root

            # Whilst "node" exists
            # This is done to get "parent" at the correct value
            while node:
                # At the end of this loop
                # "parent" will have the value of the last node
                # To get there, "node" has to iterate through the search tree with the conditions defined for the tree
                parent = node
                if node.val < val:
                    node = node.right
                else: node = node.left

            # Now that "parent" is the last node
            # It is time to add the new node
            # With similar conditions to how we iterated through the tree with "node"
            # "TreeNode(val)" assigns a new node with the value of "val"
            if parent.val < val: parent.right = TreeNode(val)
            else: parent.left = TreeNode(val)

            # Return "root" to actually return the final form of the tree
            return root
    ```

- Recursive
    ```python
    class Solution:
        def insertIntoBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:

            # If the tree doesn't exist, make a new node with the value of "val"
            if root is None:
                return TreeNode(val)

            # Traverse the tree, and call the function recursively as it navigates through the tree
            # The condition at the beginning will take care of the addition of the new node
            # As at some point, "root" will become "None"
            # It will simply add a node in that case
            if root.val < val:
                root.right = self.insertIntoBST(root.right,val)
            else:
                root.left = self.insertIntoBST(root.left,val)

            # Return the "root" every time so that the recursive calls can go through the tree
            return root
    ```
