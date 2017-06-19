# Rotate String

Tags: String, Easy

## Question

- lintcode: [Rotate String](http://www.lintcode.com/en/problem/rotate-string/)

### Problem Statement

Given a string and an offset, rotate string by offset. (rotate from left to
right)

**Example**

Given `"abcdefg"`.

    
    
    offset=0 => "abcdefg"
    offset=1 => "gabcdef"
    offset=2 => "fgabcde"
    offset=3 => "efgabcd"
    

**Challenge**

Rotate in-place with O(1) extra memory.

## Solution

This is a common reverse problem. One can use three-step reverse method. The division point is the offset position. First flip the first half, then the second half, and finally the whole string. 

> [http://blog.csdn.net/u010016196/article/details/45126853](http://blog.csdn.net/u010016196/article/details/45126853)

### Python - immutable string

```python
class Solution:
    """
    param A: A string
    param offset: Rotate string with offset.
    return: Rotated string.
    """
    def rotateString(self, A, offset):
        if not A or len(A) == 0:
            return A

        length = len(A)
        offset %= length
        before = A[:length - offset]
        after = A[length - offset:]
        A = before[::-1] + after[::-1]
        A = A[::-1]
        return A


if __name__ == '__main__':
    print Solution().rotateString('abcdef',3)
```

### Python - mutable list

```python

