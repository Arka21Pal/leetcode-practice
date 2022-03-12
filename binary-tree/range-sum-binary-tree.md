# [938. Range Sum of BST](https://leetcode.com/problems/range-sum-of-bst/)

> Given the `root` node of a binary search tree and two integers `low` and `high`, return *the sum of values of all nodes with a value in the* ***inclusive*** *range* `[low, high]`.

Simple problem, the idea being really just adding values to a variable. The easy way is to put the entire tree in a queue (the BFS approach) and pop from it.

## Solution:

Shamelessly copied from: https://leetcode.com/problems/range-sum-of-bst/discuss/1825820/Python-BFS-and-DFS-solution

```python
class Solution:
    def rangeSumBST(self, root: Optional[TreeNode], low: int, high: int) -> int:

        # Smart, putting all values from the tree into a fast queue
        q = collections.deque([root])
        # The variable we will return
        ans = 0

        while q:
            for _ in range(len(q)):
                # Pop the leftmost node
                node = q.popleft()
                if node.val >= low and node.val <= high:
                    ans += node.val
                # if node.val < low, meaning we don't have to check left anymore.
                if node.left and node.val > low:
                    q.append(node.left)
                # if node.val > high, meaning we don't have to check right anymore.
                if node.right and node.val < high:
                    q.append(node.right)
        return ans
```
