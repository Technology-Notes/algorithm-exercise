# Implement strStr

Tags: Two Pointers, String, Easy

## Question

- leetcode: [28-Implement strStr() | LeetCode OJ](https://leetcode.com/problems/implement-strstr/)
- lintcode: [lintcode - (13) strstr](http://www.lintcode.com/en/problem/strstr/)

### Problem Statement

For a given source string and a target string, you should output the **first**
index(from 0) of target string in source string.

If target does not exist in source, just return `-1`.

#### Example

If source = `"source"` and target = `"target"`, return `-1`.

If source = `"abcdabcdefg"` and target = `"bcd"`, return `1`.

#### Challenge

O(n2) is acceptable. Can you implement an O(n) algorithm? (hint: _KMP_)

#### Clarification

Do I need to implement KMP Algorithm in a real interview?

  * Not necessary. When you meet this problem in a real interview, the interviewer may just want to test your basic implementation ability. But make sure your confirm with the interviewer first.

## Problem Analysis

It's very straightforward to solve string match problem with nested for loops. Since we must iterate the target string, we can optimize the iteration of source string. It's unnecessary to iterate the source string if the length of remaining part does not exceed the length of target string. We can only iterate the valid part of source string. Apart from this naive algorithm, you can use a more effective algorithm such as KMP.

### Python

```python
class Solution(object):
    def strStr(self, haystack, needle):
        """
        :type haystack: str
        :type needle: str
        :rtype: int
        """
        # https://discuss.leetcode.com/topic/29848/my-answer-by-python/6
        # The time complexity is definitely not O(n), it is O((n-m)*m).
        # Since checking haystack[i:i+len(needle)] == needle is O(m) done O(n-m) times.
        # n - length of haystack m - length of needle
        if haystack is None or needle is None:
            return -1
        for i in range(len(haystack) - len(needle) + 1):
            if haystack[i:i+len(needle)] == needle:
                return i
        return -1

if __name__ == '__main__':
    print Solution().strStr('a', "")
```


### Source Code Analysis

1. corner case: `haystack(source)` and `needle(target)` may be empty string.
2. code convention:
    - space is needed for `==`
    - use meaningful variable names
    - put a blank line before declaration `int i, j;`
3. declare j outside for loop if and only if you want to use it outside.

Some Pythonic notes: [4. More Control Flow Tools](https://docs.python.org/3/tutorial/controlflow.html) section 4.4 and [if statement - Why does python use 'else' after for and while loops?](http://stackoverflow.com/questions/9979970/why-does-python-use-else-after-for-and-while-loops)

### Complexity Analysis

nested for loop, $$O((n-m)m)$$ for worst case.


## What is KMP?

> [https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm](https://en.wikipedia.org/wiki/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm)


