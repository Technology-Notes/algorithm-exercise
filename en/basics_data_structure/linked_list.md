# Linked List 

> [https://en.wikipedia.org/wiki/Linked_list](https://en.wikipedia.org/wiki/Linked_list)

> [https://www.tutorialspoint.com/data_structures_algorithms/linked_list_algorithms.htm](https://www.tutorialspoint.com/data_structures_algorithms/linked_list_algorithms.htm)

Linked List is a linear data structure. Unlike arrays, linked list elements are not stored at contiguous location; the elements are linked using pointers.


Linked list is a linear collection of data elements, called nodes, each pointing to the next node by means of a pointer. It is a data structure consisting of a group of nodes which together represent a sequence. Under the simplest form, each node is composed of data and a reference (in other words, a link) to the next node in the sequence. This structure allows for efficient insertion or removal of elements from any position in the sequence during iteration. 

The principal benefit of a linked list over a conventional array is that the list elements can easily be inserted or removed without reallocation or reorganization of the entire structure because the data items need not be stored contiguously in memory or on disk, while an array has to be declared in the source code, before compiling and running the program. 

On the other hand, simple linked lists by themselves do not allow random access to the data, or any form of efficient indexing.

## Code

### Python

> [http://interactivepython.org/courselib/static/pythonds/BasicDS/ImplementinganUnorderedListLinkedLists.html](http://interactivepython.org/courselib/static/pythonds/BasicDS/ImplementinganUnorderedListLinkedLists.html)

```python
class ListNode:
    def __init__(self, val):
        self.val = val
        self.next = None
```


## Basic Linked List Implementation

### Reverse a linked list

#### One-way reverse a linked list

The basic structure of the linked list is: `1 -> 2 -> 3 -> null`, after reversing it becomse `3 -> 2 -> 1 -> null`. Note that
- one will need to check whether curt is null or not when visiting the node curt.next;
- need to point the last node after reversing (the first node before reversing) to null.

### Python

> [http://www.geeksforgeeks.org/write-a-function-to-reverse-the-nodes-of-a-linked-list/](http://www.geeksforgeeks.org/write-a-function-to-reverse-the-nodes-of-a-linked-list/)

```python
# Python program to reverse a linked list 
# Time Complexity : O(n)
# Space Complexity : O(1)
 
# Node class 
class Node:
 
    # Constructor to initialize the node object
    def __init__(self, data):
        self.data = data
        self.next = None
 
class LinkedList:
 
    # Function to initialize head
    def __init__(self):
        self.head = None
 
    # Function to reverse the linked list
    def reverse(self):
        prev = None
        current = self.head
        while(current is not None):
            next = current.next
            current.next = prev
            prev = current
            current = next
        self.head = prev
         
    # Function to insert a new node at the beginning
    def push(self, new_data):
        new_node = Node(new_data)
        new_node.next = self.head
        self.head = new_node
 
    # Utility function to print the linked LinkedList
    def printList(self):
        temp = self.head
        while(temp):
            print temp.data,
            temp = temp.next

# Driver program to test above functions
llist = LinkedList()
llist.push(20)
llist.push(4)
llist.push(15)
llist.push(85)
 
print "Given Linked List"
llist.printList()
llist.reverse()
print "\nReversed Linked List"
llist.printList()
 
# This code is contributed by Nikhil Kumar Singh(nickzuck_007)


# A simple tail recursive method
# Simple and tail recursive Python program to 
# reverse a linked list
 
# Node class 
class Node:
 
    # Constructor to initialize the node object
    def __init__(self, data):
        self.data = data
        self.next = None
 
class LinkedList:
 
    # Function to initialize head
    def __init__(self):
        self.head = None
 
 
    def reverseUtil(self, curr, prev):
         
        # If last node mark it head
        if curr.next is None :
            self.head = curr 
             
            # Update next to prev node
            curr.next = prev
            return
         
        # Save curr.next node for recursive call
        next = curr.next
 
        # And update next 
        curr.next = prev
     
        self.reverseUtil(next, curr) 
 
 
    # This function mainly calls reverseUtil()
    # with previous as None
    def reverse(self):
        if self.head is None:
            return
        self.reverseUtil(self.head, None)
 
 
    # Function to insert a new node at the beginning
    def push(self, new_data):
        new_node = Node(new_data)
        new_node.next = self.head
        self.head = new_node
 
    # Utility function to print the linked LinkedList
    def printList(self):
        temp = self.head
        while(temp):
            print temp.data,
            temp = temp.next
 
 
# Driver program
llist = LinkedList()
llist.push(8)
llist.push(7)
llist.push(6)
llist.push(5)
llist.push(4)
llist.push(3)
llist.push(2)
llist.push(1)
 
print "Given linked list"
llist.printList()
 
llist.reverse()
 
print "\nReverse linked list"
llist.printList()
 
# This code is contributed by Nikhil Kumar Singh(nickzuck_007)
```


#### Doubly linked list

> [https://www.tutorialspoint.com/data_structures_algorithms/doubly_linked_list_algorithm.htm](https://www.tutorialspoint.com/data_structures_algorithms/doubly_linked_list_algorithm.htm)

> [https://en.wikipedia.org/wiki/Doubly_linked_list](https://en.wikipedia.org/wiki/Doubly_linked_list)

Doubly Linked List is a variation of Linked list in which navigation is possible in both ways, either forward and backward easily as compared to Single Linked List.

### Python

> [http://www.geeksforgeeks.org/reverse-a-doubly-linked-list/](http://www.geeksforgeeks.org/reverse-a-doubly-linked-list/)

```python
# Program to reverse a doubly linked list
 
# A node of the doublly linked list
class Node:
     
    # Constructor to create a new node
    def __init__(self, data):
        self.data = data 
        self.next = None
        self.prev = None
 
class DoublyLinkedList:
     # Constructor for empty Doubly Linked List
    def __init__(self):
        self.head = None
  
    # Function reverse a Doubly Linked List
    def reverse(self):
        temp = None
        current = self.head
         
        # Swap next and prev for all nodes of 
        # doubly linked list
        while current is not None:
            temp = current.prev 
            current.prev = current.next
            current.next = temp
            current = current.prev
 
        # Before changing head, check for the cases like 
        # empty list and list with only one node
        if temp is not None:
            self.head = temp.prev
         
    # Given a reference to the head of a list and an
    # integer,inserts a new node on the front of list
    def push(self, new_data):
  
        # 1. Allocates node
        # 2. Put the data in it
        new_node = Node(new_data)
  
        # 3. Make next of new node as head and
        # previous as None (already None)
        new_node.next = self.head
  
        # 4. change prev of head node to new_node
        if self.head is not None:
            self.head.prev = new_node
  
        # 5. move the head to point to the new node
        self.head = new_node
 
 
    def printList(self, node):
        while(node is not None):
            print node.data,
            node = node.next
 
# Driver program to test the above functions
dll = DoublyLinkedList()
dll.push(2);
dll.push(4);
dll.push(8);
dll.push(10);
 
print "\nOriginal Linked List"
dll.printList(dll.head)
 
# Reverse doubly linked list
dll.reverse()
 
print "\n Reversed Linked List"
dll.printList(dll.head)
 
# This code is contributed by Nikhil Kumar Singh(nickzuck_007)
```


### delete a node in a linked list

One will need to know its previous node therefore there must be a pointer points to its previous node. There is another kind of deletion, called ``pseudo deletion''. It means that one copies one node that is identical to the one to be deleted, and then delete. This way one does not need to know its previous node.

All one needs to do is to change `prev -> next = prev -> next -> next`. The head node might change during the above process and one can take care of it via `Dummy Node'.

> [http://opendatastructures.org/ods-python/3_2_DLList_Doubly_Linked_Li.html](http://opendatastructures.org/ods-python/3_2_DLList_Doubly_Linked_Li.html)

## Robustness of the linked list

- need to check whether curt is null when visiting curt.next
- after all the operation, one will need to check whether there is a loop. If loop exists, set one end to be null.

## Dummy Node

Dummy node is an important technique in linked list. 

The list itself has a head pointer to first node and optionally a tail pointer to last node and/or a count. With a dummy node, the first node previous pointer points to the dummy node and the last node next pointer points to the dummy node. The dummy nodes pointers can point to the dummy node itself or be null.

dummy -> head. Dummy node is usually used in singly linked list without forward pointer questions. It ensures the head wouldn't be lost during deletion. Besides, on some rare case, one uses dummy node to delete the head node. For example, Remove Doublicates From Sorted List II. THe current = current.next can not delete head element. Therefore one puts a dummy node in front of the head.

When the linked list head changes (modified or deleted), using a dummy node can simplify the code. Returning dummy.next is the new linked list.

## Fast/slow pointer

> [https://www.quora.com/What-is-a-slow-pointer-and-a-fast-pointer-in-a-linked-list](https://www.quora.com/What-is-a-slow-pointer-and-a-fast-pointer-in-a-linked-list)

Slow pointer and fast pointer are simply the names given to two pointer variables. The only difference is that, slow pointer travels the linked list one node at a time where as a fast pointer travels the linked list two nodes at a time. Given below is a basic code snippet for moving slow and fast pointers.

This concept can be used in cases like detecting a loop in a graph, finding the middle node of a linked list (better time complexity), flattening a linked list etc. All these examples use the idea of slow and fast pointers.

There are two main applications:
- quickly find the moddle node
    set up two pointer `*fast` and `*slow`. They both point to the head. `*fast` is 2 times faster than `*slow`. When `*fast` points to the end node, `*slow` is right in the middle.
- detecting a loop in the singly linked list
    same as before, set up two pointer `*fast` and `*slow` and they both pointed to the singly linked list head node. `*fast` is 2 times faster than `*slow`. If `*fast = NULL`, it means this singly linked list ends with `NULL` and there is no loop. If `*fast = *slow`, then the fast points catches up the slow one and there is a loop.

### Python

```python
class NodeCircle:
    def __init__(self, val):
        self.val = val
        self.next = None

    def has_circle(self, head):
        slow = head
        fast = head
        while (slow and fast):
            fast = fast.next
            slow = slow.next
            if fast:
                fast = fast.next
            if fast == slow:
                break
        if fast and slow and (fast == slow):
            return True
        else:
            return False
```





























