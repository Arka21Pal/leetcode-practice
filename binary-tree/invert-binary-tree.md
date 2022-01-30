# [226. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)

> Given the `root` of a binary tree, invert the tree, and return its root.

Super easy problem, literally need to just swap values of nodes. I feel dumb for not being able to do this.

## Solution (`BFS` and `DFS`)

Link: https://leetcode.com/problems/invert-binary-tree/discuss/1706957/Straightforward-DFS-and-BFS-solutions

- `BFS`
    ```python
    class Solution:
        def invertTreeBFS(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
            # Using a queue from collections instead of a list
            queue = deque([root])
            # Track all of the elements we have visited till now to prevent duplication
            visited = []

            while queue:
                # Pop the first element from the queue
                node = queue.popleft()
                # If these are unique elements
                if node and node not in visited:
                    visited.append(node)
                    # Exchange values
                    node.left, node.right = node.right, node.left
                    # Append the next values for the loop to continue
                    queue += [node.left, node.right]

            return root
    ```
- `DFS`
    ```python
    class Solution:
        def invertTreeDFS(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
            # Prevent the edge case
            if root is None:
                return root
            # Exchange values
            root.left, root.right = root.right, root.left  # invert node
            # Keep going recursively for the next values
            self.invertTreeDFS(root.left)
            self.invertTreeDFS(root.right)

            return root
    ```
