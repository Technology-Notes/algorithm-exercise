# Binary Tree

> [http://www.geeksforgeeks.org/binary-tree-set-1-introduction/](http://www.geeksforgeeks.org/binary-tree-set-1-introduction/)

A tree whose elements have at most 2 children is called a binary tree. Since each element in a binary tree can have only 2 children, we typically name them the left and right child. 

The ith level of a binary tree has at most $$2^{i-1}$$ nodes; the depth k binary tree has at most $$2^k-1$ nodes; for any binary tree T, if 

> [http://web.cecs.pdx.edu/~sheard/course/Cs163/Doc/FullvsComplete.html](http://web.cecs.pdx.edu/~sheard/course/Cs163/Doc/FullvsComplete.html)

A full binary tree (sometimes proper binary tree or 2-tree) is a tree in which every node other than the leaves has two children

A complete binary tree is a binary tree in which every level, except possibly the last, is completely filled, and all nodes are as far left as possible. 


## Code

### Python


```python
class TreeNode:
    def __init__(self, val):
        self.val = val
        self.left, self.right = None, None
```


