# [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)

> Given `head`, the head of a linked list, determine if the linked list has a cycle in it.
>
> There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that** `pos` **is not passed as a parameter**.
>
> Return `true` *if there is a cycle in the linked list*. Otherwise, return `false`.

## My Solution 1

Same as: https://leetcode.com/problems/linked-list-cycle/discuss/1710547/2-python-solutions

```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:

        # Declare an empty set
        nodes_set = set()
        # As long as head exists
        while head:
            # If "head" is in "nodes_set", that means "head" has been repeated, and a loop is confirmed
            if head in nodes_set:
                return True
            # If not, just add it
            nodes_set.add(head)
            head = head.next

        return False
```

## Solution 2

Copied from: https://leetcode.com/problems/linked-list-cycle/discuss/1710547/2-python-solutions

The idea is that we define two pointers, and if they overlap at some point, then the list has a loop

```python
class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:

        # If "head" exists
        if head:
            # Define 2 pointers
            # One is slow, and the other is fast
            slow = head
            fast = head.next

            # Checking whether the next pointers exist
            while fast and slow and fast.next:

                if fast == slow:
                    return True

                slow = slow.next
                fast = fast.next.next

        return False
```

## Solution 3

> The idea is to mark all the visited nodes. If yor revisit the same node again, then it's mean cycle is there.

This is a very good idea, I should use it sometime.

Link: https://leetcode.com/problems/linked-list-cycle/discuss/1710430/Beats-95-of-the-submission-or-Constant-Space-or-Python-Easiest-or-No-Two-Pointer

```python
class Solution(object):
    def hasCycle(self, head):

        # Defined another variable with the "head" pointer
        curr=head
        # Checking if the pointer and the next pointer exist
        if(not head or (head and not head.next)):
            return False
        # If pointer exists
        while(curr):
            # And if the value of the pointer has been marked already
            # The loop is confirmed
            if(curr.val=='V'):
                return True
            # If not, mark the pointer
            curr.val='V'
            curr=curr.next
        return False
```
