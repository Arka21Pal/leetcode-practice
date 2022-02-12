# [637. Average of Levels in Binary Tree](https://leetcode.com/problems/average-of-levels-in-binary-tree/)

<blockquote>
Given the <code>root</code> of a binary tree, return <i>the average value of the nodes on each level in the form of an array</i>. Answers within <code>10<sup>-5</sup></code> of the actual answer will be accepted.
</blockquote>

The only problem here is, how do we keep track of which level each element belongs to? The solution below uses a great approach: use dictionary keys as levels (as these are only thing common between elements in the same level), and then simply find the average from the list (which will be the value of the respective key [which are the levels themselves]).

## Solution

Copied from: https://leetcode.com/problems/average-of-levels-in-binary-tree/discuss/1733775/Faster-Than-99.85-of-Python3-using-inorder-traversal

```python
class Solution:
    def averageOfLevels(self, root: Optional[TreeNode]) -> List[float]:

        # A dictionary with lists inside it. This is how you declare it
        self.depth_dict = defaultdict(list)

        # The recursive function
        def recurse(node, d):
            if node:

                # Use the depth/level as the key and append to the value (which is a list)
                self.depth_dict[d].append(node.val)

                # recursively do this for the left and right now whilst incrementing the level (as you're going down the tree)
                if node.left: recurse(node.left, d+1)
                if node.right: recurse(node.right, d+1)

        recurse(root, 0)

        # The final list to return the average values in
        final = []

        # Find the average value for each level and append to "final"
        for value in self.depth_dict.values():
            final.append(sum(value)/len(value))
        return final
```

Another solution without recursion: https://leetcode.com/problems/average-of-levels-in-binary-tree/discuss/1762960/Python-faster-than-100-oror-iterative-oror-BFS
