# [501. Find Mode in Binary Search Tree](https://leetcode.com/problems/find-mode-in-binary-search-tree/)

> Given the `root` of a binary search tree (BST) with duplicates, return *all the [mode(s)](https://en.wikipedia.org/wiki/Mode_(statistics)) (i.e., the most frequently occurred element) in it.*
>
> If the tree has more than one mode, return them in **any order**.

The idea is extremely easy: simply iterate through each node in the tree. Keep the values and their counts in a dictionary. Check for the largest count in the dictionary, and then return all of the values which have that count.

## My solution

Link: https://leetcode.com/submissions/detail/639688055/

```python
class Solution:
    def findMode(self, root: Optional[TreeNode]) -> List[int]:

        # The dictionary in which I will store values and counts
        self.count = {}

        # The variable in which I will store the maximum count
        # It was either this, or using a list like in "max(list(self.count.values()))". I chose a variable and a loop
        self.big = 0

        # The final list which will hold all values which have a count equal to "self.big"
        self.final_list = []

        # The recursive function I'm using to go through the tree and calculate counts
        def recurse(node):

            # Only if node exists (if not, it would mean that we were at the end of the tree)
            if node:

                # If the value is already present, add to the count. Otherwise, initialise the count
                if node.val in self.count: self.count[node.val] += 1
                else: self.count[node.val] = 1

            # If the left and right nodes exist, recursively get their values in the dictionary
            if node.left: recurse(node.left)
            if node.right: recurse(node.right)

            # This is important, as without it, "self.count" will not have any value outside of this function
            return self.count

        # Call the recursive function from root
        recurse(root)

        # Put the biggest count in "self.big"
        for i in self.count.values():
            if i > self.big: self.big = i

        # Append all of the elements which have a count equal to "self.big" to "self.final_list"
        for key,value in self.count.items():
            if value == self.big:
                self.final_list.append(key)

        # Return "self.final_list", as the question requires
        return self.final_list
```

Another similar solution: https://leetcode.com/problems/find-mode-in-binary-search-tree/discuss/1319111/Easy-Python-Solution(98.91)(Recursive)
