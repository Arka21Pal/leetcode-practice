# [1305. All Elements in Two Binary Search Trees](https://leetcode.com/problems/all-elements-in-two-binary-search-trees/)

> Given two binary search trees `root1` and `root2`, return *a list containing all the integers from both trees sorted in* **ascending** *order*.

My logic is very naive, turns out I have no idea what the others have done. My idea is to simply traverse the existing trees in an in-order fashion, add them to the list, and then sort.

## Solution

```python
class Solution:
    def getAllElements(self, root1: TreeNode, root2: TreeNode) -> List[int]:
        
        # Define array to store and function to append elements to array
        s = []
        
        # Simple in-order traversal
        def all_elements(node):
            if not node: return 0

            if node.right: 
                s.append(node.right.val)
            if node.left:
                s.append(node.left.val)

            all_elements(node.right)
            all_elements(node.left)
            
        # Learnt from an edge case where one or both trees might not exist
        # I'm adding the values of the root elements manually because 
        if root1 and root2:
            s = [root1.val, root2.val]
            all_elements(root1)
            all_elements(root2)
        if not root1:
            s = [root2.val]
            all_elements(root2)
        if not root2:
            s = [root1.val]
            all_elements(root1)
            
        s.sort()
        return s
```
