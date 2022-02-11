# [671. Second Minimum Node In a Binary Tree](https://leetcode.com/problems/second-minimum-node-in-a-binary-tree/)

> Given a non-empty special binary tree consisting of nodes with the non-negative value, where each node in this tree has exactly `two` or `zero` sub-node. If the node has two sub-nodes, then this node's value is the smaller value among its two sub-nodes. More formally, the property `root.val = min(root.left.val, root.right.val)` always holds.
>
> Given such a binary tree, you need to output the **second minimum** value in the set made of all the nodes' value in the whole tree.
>
> If no such second minimum value exists, output -1 instead.

I wrote a comment for this, so I'm just going to copy-paste it from there.

The idea is very simple: recursively go through the binary tree, and add every value to a `set`. A `set` will not have duplicate values, which means, if you remove the value of the `root` from the `set`, you can simply return the `min` of the remaining elements of the `set`. Because of the way the question is worded, the `root` *has to have* the least value in the tree.

## My solution

Link: https://leetcode.com/problems/second-minimum-node-in-a-binary-tree/discuss/1763819/Super-easy-solution-for-finding-second-minimum-node

```python
class Solution:
    def findSecondMinimumValue(self, root: Optional[TreeNode]) -> int:
        # Declare a "set" so you can store values
        self.artifact = set()
        # The recursive function
        def recurse(node):
            # Check if the node exists, obviously there is no "left" and "right" for a non-existent node
            if node:
                # Add the value to the set
                self.artifact.add(node.val)
                # Recursively call the function to get every value in the set
                recurse(node.left)
                recurse(node.right)
        # Begin with the root to add all values in the set
        recurse(root)
        # If the length of the set is 1, there is only one value
        # This is why you need a set and not a list
        if len(self.artifact) == 1: return -1
        # Well, if that's not the case, remove the root value (because that will be the lowest)
        self.artifact.remove(root.val)
        # Return the minimum of what's left in the set for your answer
        return min(self.artifact)
```
