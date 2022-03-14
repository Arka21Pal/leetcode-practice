# [1022. Sum of Root To Leaf Binary Numbers](https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/)

> You are given the `root` of a binary tree where each node has a value `0` or `1`. Each root-to-leaf path represents a binary number starting with the most significant bit.
> - For example, if the path is `0 -> 1 -> 1 -> 0 -> 1`, then this could represent `01101` in binary, which is `13`.
>
> For all leaves in the tree, consider the numbers represented by the path from the root to that leaf. Return *the sum of these numbers*.

Very simple problem. Simply record the path that the node follows whilst traversing the tree, until it reaches the end of the tree. Recording these as strings into a list, then converting them back to add the values is a naive, but workable approach.

## Solution

Copied from: https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/discuss/1825744/Easy-Peasy-Recursive-Solution-converting-string-to-integer-to-binary-to-integer!-Hahah

```python
class Solution:
    def sumRootToLeaf(self, root: Optional[TreeNode]) -> int:

        # The list to keep all the recorded paths
        collect = []

        # Recursive function
        def recurse(node, path):
            if not node:
                # Stops the function when we reach the last element of the tree
                return 0

            # The reason we use a string here is because it is easy to keep it as one unit and convert later
            # If we are on a valid node, append the value of that node as the next element in the respective path
            path = path + str(node.val)

            # If neither left or right elements exist, we have reached the end of the path
            # At which point, we should append the current path to "collect", which we will use later for the answer
            if not node.left and not node.right:
                collect.append(path)
            else:
                # If we haven't reached the end of the path, keep going down both sides
                recurse(node.left, path)
                recurse(node.right, path)

        # Call the recursive function, with "path" starting as ""
        recurse(root, "")

        # Finally, calculate the sum of the all the paths in "collect"
        # Simply, convert each element in "collect" to and integer
        # Then, convert that to a binary number
        # And then convert from binary to a decimal number
        # Lastly, calculate the sum of these decimal numbers
        return sum([int(bin(int(i, 2)), 2) for i in collect])

        # The "int(i, 2)" in the middle is important without which the answer is incorrect
```
