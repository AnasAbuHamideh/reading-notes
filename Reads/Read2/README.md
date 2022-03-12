# Reading: Class 02

> [Back to the main](../../README.md)

## TDD (Test-Driven Development)

- It is a coding method that we use to validate functions we write (checking if they do what they suppose to do).

- We create multiple test units using the **assert** keyword, which assert that the given expression is True to compleate the program. It raise an error otherwise.

```
def double_it(x):
    return x**2

def test():
    assert double(5) == 10
```

---

## Script or Module

- The following is used to execute some code only if the file was run directly, and not imported

```
if __name__ == "__main__":
    print("this file is run by itself")
else:
    print("this file is run by another")
```

---

## Recursion 

- it is a programming feature allow us to call the function from its body to solve a complex problem and save time

```
def fib(n):
 
    # Stop condition
    if (n == 0):
        return 0
 
    # Stop condition 2
    if (n == 1 or n == 2):
        return 1
 
    # Recursion function
    else:
        return fib(n - 1) + fib(n - 2)
```

---