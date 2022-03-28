# [338. Counting Bits](https://leetcode.com/problems/counting-bits/)

> Given an integer `n`, return *an array* `ans` *of length* `n + 1` *such that for each* `i (0 <= i <= n)`, `ans[i]` *is the* ***number of*** `1`***'s*** *in the binary representation of* `i`.

I'm going to copy the text from the solution, as that is very well written.

> The main trick to understand is that, any even number, let's say `n` is actually obtained by left shifting the remainder of `n//2` by 1. For example:
>
> `2 -> 0010`
> `4 -> 0100`
>
> We can see that `4 = 2 << 1`. Thus for any even number n, the number of 1 bits is same as that of `n//2`.
>
> Now for odd numbers, let's say `m`, it can also be obtained by left shifting `m//2` by 1, but we also need to add an extra 1 bit. For example:
>
> `4 -> 0100`
> `9 -> 1001`
>
> We can see that `9 = (4 << 1) | 1`. Hence for any odd number `m`, the number of 1 bits is equal to the number of 1 bits in `m//2` plus 1.
>
> Thus we can build this solution from the bottom-up by just taking the number of 1 bits for 0 and 1.

## Solution

Shamelessly copied from: https://leetcode.com/problems/counting-bits/discuss/1887708/Python-oror-T%3A-O(n)-oror-S%3A-O(1)-oror-No-library-method-oror-One-Pass

```python
def countBits(self, n: int) -> List[int]:
    # Expected first values
    res = [0,1]
    # If given an edge case
    if (n <= 1):
        return res[0:n+1]
    for i in range(2,n+1):
        # For even numbers, the number of "1"s is the same as half of the number in binary form
        # For odd numbers, the number of "1"s is just one more than half of the number in binary form
        # if i%2==0, then even, else odd
        res.append(res[i//2] + res[i%2])
    return res
```
