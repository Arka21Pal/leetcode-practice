# [203. Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/)

> Given the `head` of a linked list and an integer `val`, remove all the nodes of the linked list that has `Node.val == val`, and return *the new head*.

Really simple problem, for some reason I couldn't grasp it myself.

## Solution 1

Shamelessly copied from: https://leetcode.com/problems/remove-linked-list-elements/discuss/1713448/Easy-and-intuitive-solution-using-python

```python
class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:

        # Create a placeholder node that so that we can use it to point to other nodes
        # Later for the result we are then only taking the values after the dummy node by doing dummy.next
        dummy = ListNode(-1)
        curr = dummy

        # Iterating through the linked list
        while head:

            # print(head.val)
            if head.val == val:

                # Interesting, he's able to completely derail the pointer "curr" because in the next step,
                # He can always get "curr" back on track with head
                # And because "curr" is just paving a path for "dummy", it doesn't really matter
                curr.next = None
                head = head.next
            else:
                # Here, he gets "curr" on track (or continue on the track), regardless if it was derailed or not
                curr.next = head
                # And now, because "curr" is following "head", simply iterating through with "curr" has the same effect
                curr = curr.next
                # Also updating "head" for good measure
                head = head.next

            # print(dummy)

        # Returning "dummy" because "curr" basically paved the path for it
        # And the "dummy.next" is because "dummy" was originally a placeholder
        return dummy.next
```

## Solution 2

Link: https://leetcode.com/problems/remove-linked-list-elements/discuss/1702533/Python-3-(50ms)-or-Dummy-Head-Single-Pass-Solution-or-Faster-than-99.4-or-Easy

```python
class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:

        # Eliminate the chance of empty linked lists fucking with you
        if not head:
            return None

        # The "ListNode(-1, head)" is simply saying that the next value after "ListNode(-1)" is head
        # Basically, telling the placeholder where to go next
        # Shorter version of the last solution, because here we don't actually need to use "head"
        # It knows its path already
        cur = res = ListNode(-1, head)

        # Iterating through the linked list with the variable "cur"
        # We're checking "cur.next" to make sure that we don't get an error at the end of the list (because "cur" won't know where to go)
        while cur.next:
            if cur.next.val==val:
                # Simply skip the element which matches the condition
                cur.next=cur.next.next
                continue
            # Keep iterating
            cur=cur.next

        # Same as last time, "res" was the placeholder
        # Return a modified copy of "head" (with "cur"'s help)
        return res.next
```

## Solution 3

Link: https://leetcode.com/problems/remove-linked-list-elements/discuss/1689892/Python-or-Simple-O(N)-Solution

```python
class Solution:
    def solve(head: ListNode, val: int) -> ListNode:

        # Again, two variables for modification
        result = ListNode(0)
        # dummy head
        curr = result

        # iterating over link list
        while head:
            # This time, directly add all of the matching elements from "head" to "curr"
            # Instead of "curr" removing elements
            if int(head.val) != val:
                # adding val to dummy head
                curr.next = ListNode(head.val)
                curr = curr.next
            # Keeping the loop going
            head = head.next

        # Same, return the new linked list with only selected elements
        return result.next
```
