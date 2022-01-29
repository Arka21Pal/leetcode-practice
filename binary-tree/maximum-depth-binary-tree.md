# [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

> Given the `root` of a binary tree, return *its maximum depth*.
>
> A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.

## There are three different approaches to this, which I'm going to copy from one answer.

Link: https://leetcode.com/problems/maximum-depth-of-binary-tree/discuss/1725002/Python-3-simple-solutions

1. `BFS` approach

```python
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:

        # The variable which will hold the depth
        # Incremented inside the while loop
        ans = 0
        # Edge condition
        if not root:
            return 0
        # A faster alternative to using a list
        queue = collections.deque()
        # Append the root as the first element in the queue
        queue.append(root)
        while queue:
            # Increment the depth every time the loop continues
            ans += 1
            # Another empty queue
            nextLayer = collections.deque()
            # This is an easy method to iterate through the elements stored in queue
            # And because we're popping them, it works fine
            # A similar thing could be done by directly iterating over the elements in a list
            for node in range(len(queue)):
                # Pop the first element
                cur = queue.popleft()
                # This is an important part
                # We're checking for existing elements downwards, on both the left and right side
                # At the end of the tree, ideally, there would be no elements remaining
                # Which means "nextLayer" would not have elements
                # Which means "queue" would be empty, and the while loop will stop
                if cur.left:
                    nextLayer.append(cur.left)
                if cur.right:
                    nextLayer.append(cur.right)
            queue = nextLayer
        # And because the while loop stops on time, we can accurately return the depth of the tree
        return ans
```

2. `DFS recursion` approach

```python
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        # The logic here is very simple
        # Keep going until the tree ends
        # It is caught by the simple condition "if not node: return layer"
        # The reason for that is, because we are continuously incrementing the depth of the tree with the return statement of "dfs"
        # When the function reaches the end of the tree, we should return the depth till that point
        # We are incrementing layer every time we call the function
        # The reason for the "max" return statement is because we need to go down every possible route and return the largest value of the depth
        # Because we don't know which side of the tree is longer (left or right)
        def dfs(node, layer):
            if not node:
                return layer
            return max(dfs(node.left, layer + 1), dfs(node.right, layer + 1))
        # We start the recursion with the initial parameters of "node" being "root" and "layer" being "0"
        return dfs(root, 0)
```

3. `DFS Stack` approach

```python
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        # Edge case
        if not root:
            return 0
        # Declaring variables
        ans = 0
        stack = [root]
        depth = [1]
        # Till we reach the end of the tree
        while stack:
            # Current element
            cur = stack.pop()
            # Current depth
            curD = depth.pop()
            # There are instances where one side of the tree might return the wrong depth
            # To eradicate such issues, we always take the maximum value, regardless of where the loop is
            ans = max(ans, curD)
            # append right first to pop left first. Inorder
            # No idea what that means, but to me this looks like simply appending the latest value to the lists
            # To be popped the next time the loop runs
            if cur.right:
                stack.append(cur.right)
                depth.append(curD + 1)
            if cur.left:
                stack.append(cur.left)
                depth.append(curD + 1)
        return ans
```

##  Another solution

`DFS recursion` clone: https://leetcode.com/problems/maximum-depth-of-binary-tree/discuss/1724248/Python-3-(60ms)-or-Recursive-One-Line-Max-Solution-or-Easy-to-Understand
