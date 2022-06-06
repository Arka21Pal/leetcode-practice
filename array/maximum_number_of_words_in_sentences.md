# [2114. Maximum Number of Words Found in Sentences](https://leetcode.com/problems/maximum-number-of-words-found-in-sentences/)

> A **sentence** is a list of **words** that are separated by a single space with no leading or trailing spaces.

> You are given an array of strings `sentences`, where each `sentences[i]` represents a single **sentence**.

> Return *the* ***maximum number of words*** *that appear in a single sentence*.

Super simple, just split each element in given list and find length. I modified the given list with the length of these elements instead of making a new list.

## Solution

```python
class Solution:
    def mostWordsFound(self, sentences: List[str]) -> int:

        # For the sentences in given list
        # Replace the sentence with the number of words in said sentence
        # This is done by overwriting the value of an index with the length of the array formed by splitting the sentence in the particular index
        for i in range(len(sentences)):
            sentences[i] = len([a for a in sentences[i].split()])

        # Return the highest value
        return max(sentences)
```
