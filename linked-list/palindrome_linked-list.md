# Simple: Given the `head` of a singly linked list, return `true` if it is a palindrome. 

---

Like every other person, I proceeded to convert the number into a string and checked it. Sure, it got accepted. But that's not what I'm looking for here.

My solution:

```python
class Solution:
    def isPalindrome(self, x: int) -> bool:
        return str(x) == str(x)[::-1]
```

Some other (brilliant) solutions:

## O(1) space

```python
class Solution:
    def isPalindrome(self, head: ListNode) -> bool:
        # If no element present return True
        if not head:
            return True
        
        # Get the length of the list
        len_=0
        head_ = head
        while head_:
            len_+=1
            head_=head_.next
        
        # If only one element present return True
        if len_==1:
            return True
        
        # Get the middle element
        head_ = head
        l = len_//2
        while l>=0:
            mid = head_
            head_=head_.next
            l-=1
        
        # If length is odd shift mid to one right
        if len_%2 == 1:
            mid=mid.next
        
        # Iterate 2 pointers and check if the value match at qualifying indexes
        l = len_//2
        while l>0:
            val = l-1
            tmp = head
            while val>0:
                tmp = tmp.next
                val-=1
            
            # Return False if doesn’t match
            if mid.val != tmp.val:
                return False
            mid = mid.next
            l-=1
            
        return True
```

## Mathematical solution ([link](https://leetcode.com/problems/palindrome-linked-list/discuss/906655/An-easy-mathematical-solution-9-lines))

```python
class Solution:
    def isPalindrome(self, head: ListNode) -> bool:
        n1 = n2 = 0
        t = 1
        while head:
            n1 = n1*10 + head.val
            n2 = n2 + t*head.val
            t *= 10
            head = head.next
        return n1 == n2
```

## Top sample solution (or one of them):

```python
class Solution:
    def isPalindrome(self, head: ListNode) -> bool:
        reverse = None
        fast_pt = head
        
        while fast_pt and fast_pt.next:
            fast_pt = fast_pt.next.next
            reverse, reverse.next, head = head, reverse, head.next
        
        head = head.next if fast_pt else head
        
        palindrome = True
        
        while palindrome and reverse:
            palindrome = reverse.val == head.val
            head, reverse = head.next, reverse.next
            
        return palindrome
```

I've copied these here, because why not. I'm still very much a noob, there's no way I could've thought of these lol.

---

# Some resources for linked lists in Python (which I'm probably never going to read):

- [Linked Lists in Python: An Introduction (Real Python)](https://realpython.com/linked-lists-python)
- [Linked List | Set 1 (Introduction) (GeeksforGeeks)](https://www.geeksforgeeks.org/linked-list-set-1-introduction/)

