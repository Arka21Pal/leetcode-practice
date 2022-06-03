# [1108. Defanging an IP Address](https://leetcode.com/problems/defanging-an-ip-address/)

> Given a valid (IPv4) IP address, return a defanged version of that IP address.

> A *defanged IP address* replaces every period `"."` with `"[.]"`.

There are a few methods to do this.

## Solution 1

```python
class Solution:
    def defangIPaddr(self, address: str) -> str:
        return address.replace(".", "[.]")
```

## Solution 2

Copied from: https://leetcode.com/problems/defanging-an-ip-address/discuss/1564257/two-solutions-or-one-faster-than-98-other-100

```python
class Solution:
    def defangIPaddr(self, address: str) -> str:
    
        # Adding elements to empty string in a loop
        s = ""
        for i in address:
            if i != ".":
                s += i
            elif i == ".":
                s += "[.]"
        return s
```

## Solution 3

Copied from: https://leetcode.com/problems/defanging-an-ip-address/discuss/1433164/Python-join-vs-replace-solution-one-liner

```python
class Solution:
    def defangIPaddr(self, address: str) -> str:
        return '[.]'.join(address.split('.'))
```
