# [Same Tree](https://leetcode.com/problems/same-tree/)

> Given the roots of two binary trees `p` and `q`, write a function to check if they are the same or not.
>
> Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.

Both approaches use recursion (with the first one actually being a simpler re-write of the second one)

## My solution 1

Copied from: https://leetcode.com/problems/same-tree/discuss/1597349/Python-Simple-Recursion-4-lines

```python
def isSameTree(p, q):
    if p and q:
        if p.val != q.val:
            return False
        return isSameTree(p.left, q.left) and isSameTree(p.right, q.right)
    return p == q
```

## My solution 2

Copied from: https://leetcode.com/problems/same-tree/discuss/1636646/python-beginnar-recursive

```python
class Solution(object):
    def isSameTree(self, p, q):
        if q is None and p is None:
            return True
        elif q is None or p is None:
            return False
        if p.val == q.val:
            return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```
