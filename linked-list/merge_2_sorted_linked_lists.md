# Very simple question

Given 2 linked lists (sorted), make it into one sorted linked list.

The approach is really easy:
- Form a new linked list (empty)
- Compare each value of the 2 linked lists, and create a node in the empty list == the node of list with the least value.
- Iterate through the new linked list and follow the same procedure.

Link: https://leetcode.com/problems/merge-two-sorted-lists/

## My code (unoriginal, but I at least I thought of it myself):

```python
class Solution:
    def mergeTwoLists(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        
        # Checking if either list exists, in case they decide to trip you that way.
        if not l1: return l2
        if not l2: return l1
       
        # important, create a new linked-list
        # The most important part is equating it to ListNode(-1), which essentially makes it invalid in this sense (I could've used 0 but no problem).
        # From the video which describes the approach in Java (AMAZON QUESTION), ListNode(-1) makes it an invalid linked-list, making it perfect for use in this case. I assume it's a similar thing with Python.
        
        head = dummy = ListNode(-1)
        
        while l1 and l2:
            if l1.val < l2.val: # Just comparing values, and put the lower value in the new linked-list Node.
                dummy.next = l1
                l1 = l1.next
            else:
                dummy.next = l2
                l2 = l2.next
            dummy = dummy.next
        
        # Check if any elements in either list is left. Ideally only elements in one list might be left, because either l1 is longer than l2, or vice-versa

        if l1: dummy.next = l1
        if l2: dummy.next = l2
            
        return head.next # Return head.next because head is just an invalid Node (remember NodeList(-1)?)
```

### The help I took:

- [AMAZON CODING INTERVIEW QUESTION - MERGE TWO SORTED LISTS (LeetCode)](https://www.youtube.com/watch?v=K63Mjf-H0B0)
- [Leetcode - Merge Two Sorted Lists (Python)](https://www.youtube.com/watch?v=OXmaACquVsY) - helped with the syntax.
