# [530. Minimum Absolute Difference in BST](https://leetcode.com/problems/minimum-absolute-difference-in-bst/)

> Given the `root` of a Binary Search Tree (BST), return *the minimum absolute difference between the values of any two different nodes in the tree*.

Super easy question, in fact, the only trick here is to recognise the need to use "Inorder traversal" on this tree.

The logic is simple: iterate through the tree and find the absolute minimum difference between two nodes. The catch here, is that this is a BST. The question says "any two nodes", but we know that, for such a question, we would most definitely need a list of some sort (which was what I originally tried and failed). However, because this is a BST, this difference can actually be computed on the fly. The point is, a BST will always have lesser elements on the left side, and greater elements on the right side. Which means we don't need to check literally element for their difference; we can just check the current and previous element! This is because if you have a subtree (one element leading to a "left" and "right" element), the left element will definitely be lesser than the current element, whilst the opposite will be true for the element on the right. With that, the values of these will also be influenced by which side of the root they are on. Thus, considering everything, we practically just need to compare adjacent elements whilst recursively going through the elements in the tree.

In my approach, I define two variables in the `__init__` function, and use them to store values in the main, recursive function.

Note the way `inorder` traversal has been implemented, this is important and will definitely help me in my interviews.

## Solution

Copied from: https://leetcode.com/problems/minimum-absolute-difference-in-bst/discuss/1734825/inorder-of-BST-to-solve-the-problem..

```python
def __init__(self):
    self.prev = None
    self.mindiff=math.inf
def getMinimumDifference(self, root: Optional[TreeNode]) -> int:
    # Defining the recursive function to implement inorder traversal and go through the BST
    def inorder(node):
        # Only if node exists
        if node:
            # First part of inorder traversals, recursively move right
            inorder(node.right)
            # "self.prev" was defined before, but in the loops after, it will have a value other than None
            if self.prev != None:
                # Simply finding the minimum value out of the current difference and previous value
                self.mindiff = min(self.mindiff, abs(prev.val-node.val))
            # Giving previous the value of the node after the loop above so that it has the "previous" value in the next loop
            self.prev = node
            # Second part of inorder traversal, recursively move left
            inorder(node.left)
    # Call the recursive function
    inorder(root)
    # Return the final difference
    return self.mindiff
```
