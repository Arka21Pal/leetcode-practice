# [108. Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

> Given an integer array `nums` where the elements are sorted in **ascending order**, convert *it to a* ***height-balanced*** *binary search tree*.
>
> A height-balanced binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.

I feel ashamed that I wasn't able to do this by myself. The logic isn't too complicated, and it is simply a case of recursion/iteration.

The logic is:\
The element in the middle of the list will be the `root` node. Thus, we will split the original list into two, on either side of the middle element.\
With that said, we will be repeating this process for the now halved lists, because even for them, we need to have, sort of a "central" node from which other nodes will branch out. Thus, it becomes the same process as the first time, making it ideal for a recursive solution.

## Solution

Shamelessly copied from: https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/discuss/1704702/Simple-Recursion

```python
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:

        # Taking the length of the list
        # This is important, because the length of the list changes with every iteration of the loop
        n = len(nums)

        # If the list has more than one element
        if n > 1:

            # Define another root, just for this specific sub-branch
            # Of course, the original root contains the entire tree as a sub-branch
            # Thus, it works for all levels of "root"s
            root = TreeNode(nums[n // 2])

            # Split the list, and define the left and right nodes
            # By the logic of a BST; lesser values on the left and greater values on the right
            root.left = self.sortedArrayToBST(nums[:n//2])
            root.right = self.sortedArrayToBST(nums[1 + (n//2) :])

            # Return the root, as without it the recursion will not work
            return root

        # If the list has a single element left, return a TreeNode with the value of the element
        elif n == 1:
            return TreeNode(val = nums[0])

        # But if nothing matches, return None
        else:
            return None
```

## Solution 2 (super short gem)

Shamelessly copied from: https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/discuss/1670770/Python3-Solution-or-3-line-solution

```python
class Solution:
    def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:
        # If no elements in the list, return None
        if len(nums) == 0: return None
        # Halve the length of the list every time, just like in the original solution
        n = len(nums)//2
        # Return the "TreeNode" with left and right nodes by calling the function recursively
        # For every value in the middle of every new list (which changes whenever the recursive call is successful)
        return TreeNode(nums[n],self.sortedArrayToBST(nums[:n]),self.sortedArrayToBST(nums[n+1 :]))
```

### Other solutions which have the same basic idea:
- https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/discuss/1685840/Min-Memory-and-easy-to-understand
- https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/discuss/1681534/Python-Intuitive-O(n)-explained-Approach-and-Big-O-analysis
