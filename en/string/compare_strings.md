# Compare Strings

Tags: Basic Implementation, String, LintCode Copyright, Easy

## Question

- lintcode: [Compare Strings](http://www.lintcode.com/en/problem/compare-strings/)

### Problem Statement

Compare two strings A and B, determine whether A contains all of the
characters in B.

The characters in string A and B are all **Upper Case** letters.

#### Notice

The characters of B in A are not necessary continuous or ordered.

**Example**

For `A = "ABCD"`, `B = "ACD"`, return `true`.

For `A = "ABCD"`, `B = "AABC"`, return `false`.

## Solution

Similar to [Two Strings Are Anagrams](http://algorithm.yuanbin.me/zh-hans/string/two_strings_are_anagrams.html). Now we want to check whether all the characters in B are in A, but not individual character. For example, there are two ``A`` in B="AABC" but only one ``A`` in A="ABCD". Therefore the return value should be false. Make sure to check with the interviewer.

It is not suitable to use double loops as in strstr. Note also that the characters in string A and B are all **Upper Case** letters. It is easy to get that one will need to get the frequency by iterating over A and B first, and then compare frequencies. Well, let us use Hash table. 


### Python

```python
class Solution:
    """
    @param A : A string includes Upper Case letters
    @param B : A string includes Upper Case letters
    @return :  if string A contains all of the characters in B return True else return False
    """
    def compareStrings(self, A, B):
        #letters =   collections.defaultdict(int)
        letters = {}
        for a   in  A:
            if a not in letters:
                letters[a]  =  1
            else:
                letters[a] += 1
        for b in B:
            if b not in letters:
                return False
            else:
                letters[b] -= 1
            if letters[b] < 0:
                return False
        return True

if __name__ == '__main__':
    print Solution().compareStrings("AABC", "ABCD")
```

or use collections defaultdict

```python
import collections
class Solution:
    """
    @param A: A   string  includes    Upper   Case    letters
    @param B: A   string  includes    Upper   Case    letters
    @return : if  string A contains all of the characters in B return  True else return False
    """
    def compareStrings(self,    A,  B):
        letters =   collections.defaultdict(int)
        for a   in  A:
            letters[a]  +=  1
        for b in B:
            letters[b] -= 1
            if letters[b] < 0:
                return False
        return True

if __name__ == '__main__':
    print Solution().compareStrings("AABC", "ABC")





```

### Analysis

Python `dict` is a hash and it is very convinent to use hash. collections is also very useful but more difficult to analysi the complexity.

1, if len(B) > len(A) then `false`, including empty character.
2, use extra space to store the frequency

### complexity

loop through A, loop through B, the time complexity is $$O(n)$$ the worst, space complexity is $$O(1)$$.


