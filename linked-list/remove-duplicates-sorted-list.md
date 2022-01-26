# [83. Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)

> Given the `head` of a sorted linked list, *delete all duplicates such that each element appears only once*. Return *the linked list **sorted** as well*.

Easy problem, however the sticking point here is that `head` is the only variable that knows what its `next` is. Thus, while declaring any other variable, we need to explicitly set `variable.next` = `head.next`.

## My solution

Shamelessly copied from another solution: [python simple solution time O(N) space O(1)](https://leetcode.com/problems/remove-duplicates-from-sorted-list/discuss/1492445/python-simple-solution-time-O(N)-space-O(1))

```python
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:

        # Return head if head or head.next don't exist. Condition set for non-existent arrays.
        if not head or not head.next: return head

        # Set two variables. Here, prev is the dummy variable, while origin keeps track of all the elements that head traverses.
        prev, origin = None, head

        while head:

            # Always set prev=head in the beginning to then use after the loop.
            prev = head

            # Check whether head.next exists and for common elements.
            while head.next and head.val == head.next.val:
                # If the next element is common, simply skip the current element. The variable origin keeps track of this anyway.
                head = head.next

            # Explicitly declare the next value of prev, otherwise prev doesn't know where to go next.
            prev.next = head.next

            # A test I tried to check if the loop to skip values was working.
            # print(prev.val)

            # Finally, iterate to the next value of head.
            head = head.next

        # Return the variable which keeps track of the value of head. I learnt this because head returns [0]
        return origin
```

## Solution 2

Link: https://leetcode.com/problems/remove-duplicates-from-sorted-list/discuss/1718548/Clean-Recusrsion

```python
class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:

        # Return "head" if it doesn't exist
        if not head:
            return head

        # If a duplicate element is found
        if head.next and head.val == head.next.val:
            # Skip the element by calling the original function again, but set the value of this element as the next element
            head = self.deleteDuplicates(head.next)
        else:
            # If not, simply set the value of the next value with calling the function for the next element
            head.next = self.deleteDuplicates(head.next)

        # This is the reason this works
        # At the end of all of the recursive loops, the function will finally return "head"
        # Which means all of the elements which have been skipped, will now have the value of the next element automatically
        # And the elements not skipped, will also have the correct values
        # Without this statement, this approach of recursion wouldn't have worked

        return head
```

I didn't clearly understand this solution however.

## Resources:
Some other solutions,
- [[Python] Beats 95.13%](https://leetcode.com/problems/remove-duplicates-from-sorted-list/discuss/1491405/Python-Beats-95.13)
- [Simple Python Solution: Faster than 95%](https://leetcode.com/problems/remove-duplicates-from-sorted-list/discuss/1478176/Simple-Python-Solution%3A-Faster-than-95)
