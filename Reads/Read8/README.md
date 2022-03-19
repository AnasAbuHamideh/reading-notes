# List Comprehension
Chances are you’ll use a lot of lists as a Python programmer. While we’re all big fans of for loops (and nested for loops), Python provides a more concise method for handling lists and list comprehension. 

In order to keep your code elegant and readable, it’s recommended that you use Python’s comprehension features.

List comprehension is a powerful and concise method for creating lists in Python that becomes essential the more you work with lists, and lists of lists.

Syntax
Consider the following example:

my_new_list = [ expression for item in list ]

You can see from this example that three ingredients are necessary for a python list comprehension to work.

1. First is the expression we’d like to carry out. expression inside the square brackets.
2. Second is the object that the expression will work on. item inside the square brackets.
3. Finally, we need an iterable list of objects to build our new list from. list inside the 
   square brackets.

To understand the list comprehension, imagine it like this: you’re going to perform an expression on each item in the list. The expression will determine what item is eventually stored in the output list. 

You are here: Home / Basics / List Comprehensions in Python
List Comprehensions in Python
Author: Josh Petty
Last Updated: August 30, 2021

Table of Contents
Syntax
Create a List with range()
Create a List Using Loops and List Comprehension in Python
Multiplying Parts of a List
Show the first letter of each word using Python
Lower/Upper case converter using Python
Print numbers only from a given string
Parsing a file using list comprehension
Using functions in list comprehensions
In conclusion
Related Posts
Chances are you’ll use a lot of lists as a Python programmer. While we’re all big fans of for loops (and nested for loops), Python provides a more concise method for handling lists and list comprehension. 

In order to keep your code elegant and readable, it’s recommended that you use Python’s comprehension features.

List comprehension is a powerful and concise method for creating lists in Python that becomes essential the more you work with lists, and lists of lists.



### Syntax
Consider the following example:

my_new_list = [ expression for item in list ]

You can see from this example that three ingredients are necessary for a python list comprehension to work.

First is the expression we’d like to carry out. expression inside the square brackets.
Second is the object that the expression will work on. item inside the square brackets.
Finally, we need an iterable list of objects to build our new list from. list inside the square brackets.
To understand the list comprehension, imagine it like this: you’re going to perform an expression on each item in the list. The expression will determine what item is eventually stored in the output list. 


Not only can you perform expressions on an entire list in a single line of code, but, as we’ll see later, it’s possible to add conditional statements in the form of filters, which allows for more precision in the way lists are handled.

### Notes about Lists Comprehensions
List comprehension methods are an elegant way to create and manage lists. 
In Python, list comprehensions are a more compact way of creating lists. 
More flexible than for loops, list comprehension is usually faster than other methods.