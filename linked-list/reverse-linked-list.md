# [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

> Given the `head` of a singly linked list, reverse the list, and return *the reversed list*.

## Solution 1

Link: https://leetcode.com/problems/reverse-linked-list/discuss/1704103/Python-3-(40ms)-or-3-Lines-Only-or-Iterative-Approach-Easy-Solution

```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        # Defining the variables
        cur, prev = head, None

        # The idea here is;
        # "prev" starts from Null, i.e. after the linked list
        # If "curr.next" is equal to "prev"
        # Then "curr" actually goes back an element
        # Thus, when "prev = curr", "prev" becomes the previous element
        # And then, to keep the loop going, we give the next value to "curr"

        while cur:
            cur.next, prev, cur = prev, cur, cur.next
        return prev
```

Problem: why doesn't this solution work when I split up the lines and write them separately? Like;

```python
cur.next = prev
prev = cur
cur = cur.next
```

## Solution 2

Link: https://leetcode.com/problems/reverse-linked-list/discuss/1715680/Reversing-a-linked-list-with-the-help-of-Python-list

```python
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:

        # Empty list
        older = []

        # If linked list doesn't exist
        if head==None:
            return head

        #In case of only one node present in lisked list
        if head.next==None:
            return head

        #In case of multiple nodes
        temp=head
        while temp is not None:
            # Just store the values as they come whilst iterating through the list
            older.append(temp.val)
            temp=temp.next

        #Reversing the list
        temp=head
        while temp is not None:
            # Because "pop()" removes the last element of the list
            # It acts as a "LIFO" setup: thus, the list is reversed because the order of the elements was same as the original linked list
            temp.val=older.pop()
            temp=temp.next

        return head
```
