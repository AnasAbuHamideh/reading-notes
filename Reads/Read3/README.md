# Reading: Class 03

> [Back to the main](../../README.md)

## Reading/Writing Files

| Mode | Description |
| - | - |
| ‘r’ | Default mode, opens file for reading |
| ‘w’ | Opens file for writing. If the file doesn’t exist, it creates it. Otherwise, it open the file. Once opened, it deletes everything was inside it. |
| ‘x’ | Create a new file, if it is already exist, the operation failed |
| ‘a’ | Opens file in append mode, so it will not delete the previous contents. If the file doesn’t exist, it creates it |
| ‘t’ | Default mode, opens in text mode |
| ‘b’ | Opens in binary mode |
| ‘+’ | Opens the file for reading and writing |

---

- Reading files

        file = open(“path”, ‘r’) 

    we want to read from that file

    the (path) has to be a full path to the file, or just the name of the file if it was in the same directory of the python file

        file = open(“path”, ‘r’, encoding=’utf-8’) 

    if we have another language but English in that file and we want from python to process it

        with open(‘test.txt') as reader:
            print(reader.read())

    we use the (with as) statement to open a file and use it inside the scope of (with) as the variable we define, so (reader) will hold the value of (open(‘test.txt'))

        file = open(‘test.txt')
        file.read() 

    it returns all the contents of the text file as a string 

        list(file.readlines()) 

    it returns all the lines of the text file as a list 

        file.readline() 

    it returns the next line in the file, if you put in a loop, it will get he whole file line-by-line

        file.readline(14)

    it returns the first 14 characters(index) in the file

  - we can print everything in the file by many ways:

        for line in file:
            print(line, end='')

    or

        print(file.read())

    or

        line = file.readline()
        while line != “”:  
            print(line, end='')
            line = file.readline()

---

- Closing files

        file.close()

    it will close the file, NOTE: we must always close any file we open after we finish working on it  

        file.closed 

    returns rather the file is closed or not

---

- Writing on files

  - Overwriting mode
  
        file = open(“test.txt”, ‘w’) 

    open that file to write on it (on the writing mode), BUT it will delete all the previous contents of the file

  - Appending mode

        file = open(“test.txt”, ‘a’) 

    open that file to write on it (on the appending mode), that means it won’t delete anything from the previous data of the file, but we can add to it

    ---

        file.write(“message”) 

    it will write that string on the file 

        file.writelines([“hello”, “world”, “!”]) 

    it will write all the elements of the list on the file 

        file.flush() 

    it will delete all the data from the file 

        file.fileno() 

    it will delete all the data from the file 

    ---

  - Working on two files at the same time

        with open(“test1.txt”, 'r') as reader, open(“test1.txt”, 'w') as writer: 
            writer.writelines(reader.readlines())

---

- Special magic functions

    we can create a class reader to handle the opening and closing processes automatically

```
class my_file_reader():
    def __init__(self, file_path):
        self.path = file_path
        self.file_object = None

    def __enter__(self):
        self.file_object = open(self.path)
        return self

    def __exit__(self, type, val, tb):
        self.file_object.close()
```

the function `__enter__` is invoked when calling the (**with**) statement

the function `__exit__` is invoked when exiting the (**with**) statement’s block

    with my_file_reader(“test.txt”) as reader:
        print(reader.file_object.readlines())

---

## Handling Errors

- Types of errors

    - NameError: the name of the variable, function or class isn’t defined  

    - TypeError: an error in handling a type of data

    - SyntaxError: an error in the wrote syntax (invalid syntax)

    - ZeroDivisionError: an error due to dividing integer by zero (either using / or %) 

    - AssertionError: an error raised due to a false expression in an (assert) statement 

    - Exception: an error raised intentionally by the code using the (raise) statement

---

- (Try/Except) syntax

we use it to prevent the program from cashing( stopping because detecting an error ) when some error occurred 

```
try: 
 	pass
except:
  	pass
else: 	
      	pass
finally: 
 	pass
```

The program will do the (try) statement first, if it has successfully executed, the statements in (else) will be executed too, the (else) statement is optional

But if any error occurs during executing the (try) statement, then the (except) statement will be executed and no errors will crash the program 

The (finally) statement will be executed anyway

---

- Multiple errors : if the first instruction had an error, the first except will execute its statement, but if an outsider error (outside the try) occurs, the second except will execute its statement

```
try: 
 	pass
except:
  	pass
except:
  	pass
```

---

- Assertion

        assert (expression)

    it will complete the program if the expression is true (it is asserting that the expression is true), but raise an assertion error if the expression is false

---

- Raising exceptions

        raise Exception("Sorry, no numbers below zero")

    that will raise an exception error and crash the program

        raise TypeError("Only integers are allowed")

    that will raise typo error and crash the program

---