# [112. Path Sum](https://leetcode.com/problems/path-sum/)

> Given the `root` of a binary tree and an integer `targetSum`, return `true` if the tree has a *root-to-leaf* path such that adding up all the values along the path equals `targetSum`.

> A *leaf* is a node with no children.

The easiest approach to this would be recursion.

The logic here is simple:\
We simply need to go through the elements in the tree, and check if adding these elements equals to the `targetSum`.

In the first solution,
- We define a function which we will call recursively.
- Then, we check if the node exists.
- After that, we increment the value of "total" by the value of the current node.
- We check if we have reached the end of the tree, and if the sum of values matches `targetSum`.
- Because we need to cover every node in the tree, we define two variables, one handling the left side, and the other handling the right side of the tree.
    - This is only possible because we start with the root as the `node` (end of the program).
- Then, we return either of the two variables, because even if one of them gets the desired result (a total value that matches the target), then our objective is fulfilled.
- Finally, we start with the `node` being `root` and the `total` being `0`.

In the second solution,
- The idea is the same as in the first solution, but we use a few different methods of implementation.
- The main difference here is the usage of the `deque` class instead of the `leftMatch` and `rightMatch` variables which we used in the first solution.
- So, every time the loop runs, we append the next value of the node and the remaining difference between the target and the current value, to a stack.
- Instead of holding the left and right node values and the subsequent recursion that comes with it, we simply append the values of the left and right nodes to the stack. Because we keep popping the stack every time the loop runs, we stay up-to-date and do not miss elements.
- Some parts are the same, like checking if the addition of our elements matches `targetSum` at the end of the tree.

Overall, iteration is easier to understand, however recursion is easier to implement.

## Solution 1

Copied from: https://leetcode.com/problems/path-sum/discuss/1696898/Python-or-Recursive-or-Easy-to-read

```python
class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root:
            return False

        def hasMatchingSum(node, total):
            # Return False if the tree doesn't exist
            if node is None:
                return False

            # Tracking the total
            total += node.val

            # Check if the targetSum is achieved by the end of the tree
            if node.left is None and node.right is None:
                return total == targetSum

            # Call the function recursively to calculate for both sides of every node
            leftMatch = hasMatchingSum(node.left, total)
            rightMatch = hasMatchingSum(node.right, total)

            # Assuming either one, or both get it right
            return leftMatch or rightMatch

        return hasMatchingSum(root, 0)
```

## Solution 2

An iterative, `DFS` solution.

Link: https://leetcode.com/problems/path-sum/discuss/1661687/Python-or-Iterative-DFS-using-Deque

```python
class Solution:
    def hasPathSum(self, root: Optional[TreeNode], targetSum: int) -> bool:
        if not root:
            return False
        # "dequeue" instead of list
        st = collections.deque()
        # Append both the starter node and the remaining value
        st.append((root, targetSum-root.val))
        while st:
            # Pop it every time so that "st" remains clean
            n, v = st.pop()
            # If there's no node left at the end
            # And the targetSum has been acheived, return True
            if not n.left and not n.right and v == 0:
                return True
            # If left node exists, append that and the remaining value
            if n.left:
                st.append((n.left, v-n.left.val))
            # If right node exists, append that and the remaining value
            if n.right:
                st.append((n.right, v-n.right.val))
        return False
```
