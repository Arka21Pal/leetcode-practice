# [232. Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)

> Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (`push`, `peek`, `pop`, and `empty`).

This is actually quite easy. And my solution doesn't work. For some reason which I don't understand. Whatever.

## My defunct solution

I wonder why this doesn't work.

```python
class MyQueue:

    def __init__(self):
        self.stack = []

    def push(self, x: int) -> None:
        self.stack.append(x)

    def pop(self) -> int:
        # They wanted the first element
        return self.stack[::-1].pop()

    def peek(self) -> int:
        # Again, wanted the first element
        return self.stack[0]

    def empty(self) -> bool:
        return self.stack == []


# Your MyQueue object will be instantiated and called as such:
# obj = MyQueue()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.peek()
# param_4 = obj.empty()
```

## Working solution

Link: https://leetcode.com/problems/implement-queue-using-stacks/discuss/1721622/Pyhton-Implimentation

```python
class MyQueue:

    # Initialising two stacks, because the question asked for it (and some test cases will fail as I will explain)
    def __init__(self):
        self.s1 = []
        self.s2= []

    # Obviously
    def push(self, x: int) -> None:
        self.s1.append(x)

    # Very easy to understand, we're simply putting all elements of "s1" into "s2"
    # We're doing that in reverse, because the question wants us to remove the first element of the list instead of the last
    # So, we pop "s2" for the result
    # This could technically be done by a one-liner like "self.s1[::-1].pop()" but that doesn't work with a test case
    def pop(self) -> int:
        if self.s2 :
             return self.s2.pop()
        elif self.s1 :
            while self.s1:
                # Popping "s1" and appending to "s2" lets us reverse the order of elements from "s1" to "s2"
                self.s2.append(self.s1.pop())
            return self.s2.pop()
        return null

    # Same logic, always return "s2" instead of "s1"
    # As they want the first element, return the last element of "s2"
    def peek(self) -> int:
        if self.s2 :
             return self.s2[-1]
        elif self.s1 :
            while self.s1:
                self.s2.append(self.s1.pop())
            return self.s2[-1]
        return null

    # Basically, invert the truth
    def empty(self) -> bool:
        return not self.s1 and not self.s2


# Your MyQueue object will be instantiated and called as such:
# obj = MyQueue()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.peek()
# param_4 = obj.empty()
```
