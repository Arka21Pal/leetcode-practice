# [653. Two Sum IV - Input is a BST](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/)

> Given the `root` of a Binary Search Tree and a target number `k`, return *`true` if there exist two elements in the BST such that their sum is equal to the given target*.

Simple problem: append elements which have been iterated through, into a stack. Check for the difference between the target and the current element in that list. If the difference is not present till the end of the tree, return "False".

## Solution

Copied from: https://leetcode.com/problems/two-sum-iv-input-is-a-bst/discuss/1725677/Easy-solution

```python
class Solution:
    def findTarget(self, root: Optional[TreeNode], k: int) -> bool:
        # Empty stack to keep the nodes
        # A set to keep the values
        stack = collections.deque()
        values = set()
        head = root
        stack.append(head)

        # As long as there are elements in the stack (i.e. we haven't reached the end of the tree yet)
        while stack:
            # Take the node at the beginning of the stack, thus going in order
            node = stack.popleft()
            # Checking for the difference in the set
            if (k - node.val) in values:
                return True
            # Add the value of the node to the set to aid in checking in the next loop
            values.add(node.val)
            # Add both left and right nodes to the stack
            if node.left:
                stack.append(node.left)
            if node.right:
                stack.append(node.right)
        return False
```

Another solution which basically does the same thing: https://leetcode.com/problems/two-sum-iv-input-is-a-bst/discuss/1725677/Easy-solution
