# Group Anagrams

Tags: Hash Table, String, Medium

## Question

- leetcode: [Group Anagrams](https://leetcode.com/problems/group-anagrams)
- lintcode: [Group Anagrams](http://www.lintcode.com/en/problem/anagrams/)

### Problem Statement

Given an array of strings, group anagrams together.

For example, given: `["eat", "tea", "tan", "ate", "nat", "bat"]`,  
Return:
    
    [
      ["ate", "eat","tea"],
      ["nat","tan"],
      ["bat"]
    ]

**Note:** All inputs will be in lower-case.

## Solution

In [Two Strings Are Anagrams](http://algorithm.yuanbin.me/zh-hans/string/two_strings_are_anagrams.html), we introduced the methods using sorting and hashmap to check the anagrams. Here we will use these two methods simutaneously. One can loop through the strings twice, one for sorting and one for saving the final results. 

Alternatively, in Python, one can do sorting and hashmap saving in one loop, using ``get`` method

### Python 

```python
class Solution(object):
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        dictStrs = {}
        for str in strs:
            ls = tuple(sorted(str))
            print "ls", ls
#            if not dictStrs.has_key(ls):
#                dictStrs[ls] = []
#            dictStrs[ls].append(str)
#   The method get() returns a value for the given key. If key is not available then returns default value None.
            dictStrs[ls] = dictStrs.get(ls, []) + [str]
            print "dictStrs", dictStrs

#        resStrs = []
#        for group in dictStrs.values():
#            resStrs.append(group)
#
#        return resStrs
        return dictStrs.values()

if __name__ == '__main__':
    print Solution().groupAnagrams(["eat", "tea", "tan", "ate", "nat", "bat"])
```

### Code analysis

Construct key as  character string, value as the hashmap counting. It is straightforward to sort character strings in Python. It is also easy to construct the hashmap sing `get` method.

### Complexity analysis


