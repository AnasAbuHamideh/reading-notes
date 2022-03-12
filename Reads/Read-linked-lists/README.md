# Reading: Class 05 : Linked lists

> [Back to the main](../../README.md)

## Definition

- linked list is a list of connected nodes 
- a node consists of piece of data and a pointer that reference (points) to the next node
- the last node in the list reference to the value (null)
- each node can only see (reach) the next node
- the first node called the (Head)

---

## Linear vs Non-linear

- linear linked list: 

    it is a linked list where each node in it points only to one single other node, the one next to it (in front of it)

- non-linear linked list: 

    it is a linked where nodes in it can point to more than one other node

---

## Singly vs Doubly vs Circular

- singly linked list: 

    it is a list where each node only reference to the one in front of it till the last one that reference to (null)

- doubly linked list: 

    it is a list where each node reference to its both next and previous ones, the first one reference only to the next, and the last one reference to (null)

- circular linked list: 

    it is a list where each node only reference to the one in front of it till the last one that reference to one of the nodes to form a circle

---

## Inserting a node 

- Insert at the beginning : 

    - create the new node

    - direct its pointer to the second node (the one after the Head)

    - direct its Head’s pointer to the new one 

- Insert at the end : 

    - create the new node

    - direct its pointer to the last node 

    - direct its last node’s pointer to (null)

- Regular list vs Linked list

    - Regular list

        - it stores data in memory in a sequential form
        - inserting and deleting can be really slow
        - searching is fast
        - static size and hard to grow or shrink
        - finding elements is fast, we can also use binary search
        - **helpful** when:
            - you do know the size of the list 
            - you need random access to elements
            - you want to iterate quickly 

- Linked list
    - it stores data in memory in randomly 
    - inserting and deleting can be really fast
    - searching is slow
    - dynamic size and easy to grow or shrink
    - finding elements is slow, we cannot use binary search
    - **helpful** when:
        - you don’t know the size of the list 
        - you want to add or remove quickly
        - you don’t want a random access 


---