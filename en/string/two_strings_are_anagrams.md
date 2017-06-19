# Two Strings Are Anagrams

Tags: String, Cracking The Coding Interview, Easy

## Question

- lintcode: [Two Strings Are Anagrams](http://www.lintcode.com/en/problem/two-strings-are-anagrams/)

### Problem Statement

Write a method `anagram(s,t)` to decide if two strings are anagrams or not.

**Clarification**

What is **Anagram**?  
\- Two strings are anagram if they can be the same after change the order of
characters.

**Example**

Given s = `"abcd"`, t = `"dcab"`, return `true`.  
Given s = `"ab"`, t = `"ab"`, return `true`.  
Given s = `"ab"`, t = `"ac"`, return `false`.

**Challenge** ****

O(n) time, O(1) extra space


## Solution 1 - hashmap string frequency

To check if two strings are anagrams or not, considering upper/lower cases and empty characters, one can check if the frequency of different characters are the same for two strings. For questions of comparing the number of characters, the usual way is to loop through two strings, get the frequencies. If they are not equal, then return `false`. Many simply string interview questions are based on this.

### Python

``` python
class Solution:
    """
    @param s: The first string
    @param b: The second string
    @return true or false
    """
    def anagram(self, s, t):
        return collections.Counter(s) == collections.Counter(t)
```

## Solution 2 - order the strings

Alternative solution is to order the strings first. If the ordered strings are identical, then they are anagrams.


### Python


```python
class Solution:
    """
    @param s: The first string
    @param b: The second string
    @return true or false
    """
    def anagram(self, s, t):
        return sorted(s) == sorted(t)
```

## Source code analysis

Order s and t strings and then compare. 

## Reference

- *CC150 Chapter 9.1* Chinese Edition p109
