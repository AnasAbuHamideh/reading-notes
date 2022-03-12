# Reading: Class 04

> [Back to the main](../../README.md)

---

## Defining a class:

    class MyClass:
        pass

---

## Instances of the class:

    obj1 = MyClass() 

defines an object (instance) of the class

    isinstance(var1, class1) 

it will return (True) if the variable (var1) is differentiated from the class (class1). Otherwise, it will print (False)

    del obj1

that will delete the object  

---

## Class constructor:

it is the main function inside the class that will be run automatically every time we define an instance of the class

it is defined by default without parameters in any class:

    class MyClass:
        def __init__(self)
            pass

we can add parameters to the class:

    class MyClass:
        def __init__(self, par1, par2)
            pass

and we have to fill the arguments in the instance we define:

    MyClass(5, 2)

---

## Class attributes:

attribute is any variables defined directly inside the class (not inside its methods)

Defining an attribute:

    class MyClass:
        x1 = “Hi”

Using an attribute inside the class (using “self”):

    class MyClass:
        x1 = 50
        x2 = self.x1 + 20

Using an attribute outside the class (using the object):

    class MyClass:
        x1 = 50

    obj1 = MyClass()
    print( obj1.x1 )

Deleting an attribute:

    class MyClass:
        x1 = 50

    obj1 = MyClass()
    del obj1.x1

---

## Class methods:

method is any function defined inside the class (including the constructor)

The “self” parameter: we have to add the parameter “self” as the first parameter to any method we define, it passes the object itself inside the class. Whenever we want to use any attribute inside the class, we have to use the “self” word to reach the attribute of the current used object

Defining a method:

    class MyClass:
        x = 50
        def func(self, y)
            return self.x + y

Using a method inside the class (using “self”):

    class MyClass:
        x = 50
        def func(self, y)
            return self.x + y
        def func2(self)
            self.func(20)

Using a method outside the class (using the object):

    class MyClass:
        x = 50
        def func(self, y)
            return self.x + y

    obj1 = MyClass()
    print( obj1.func(20) )

Types of attributes and methods

- Public: the public attribute or method can be reached from inside the class using the “self” word, or from outside the class using the object instance 

        class MyClass:
            myPublicAtrr = “ I’m a public attribute ”
            def myPublicFunc(self)
                print(“ I’m a public method ”)
                print(myPublicAtrr)

        obj1 = MyClass()
        print(obj1.myPublicAtrr)
        obj1.myPublicFunc()

- Semipublic (Protected): the protected attribute or method can be reached from inside and outside the class, but we can’t use it outside the current python file even if we import it in another one, but we can use them freely outside the class in this file, we can define them by adding the underscore ( _ ) before their names, we also have to use the underscore to reach the attribute or the method

        class MyClass:
            _myProtectedAtrr = “ I’m a protected attribute ”
            def _myProtectedFunc(self)
                print(“ I’m a protected method ”)
                print(_myProtectedAtrr)

        obj1 = MyClass()
        print(obj1._myProtectedAtrr)
        obj1._myProtectedFunc()

- Private: the private attribute or method cannot be reached from outside the class or this file even if we import it in another one, we can define them by adding the double underscore ( __ ) before their names, we usually use a public (setter) and (getter) methods inside the class which can reach and modify the private attributes so we can call them from outside the class

        class MyClass:
            __myPrivateAtrr = “ I’m a private attribute ”
            def __myPrivateFunc(self)
                print(“ I’m a private method”)
                print(__myPrivateAtrr)
            def mySetter(self, value):
                __myPrivateAtrr = f“ changed to {value} ”
            def myGetter(self):
                return __myPrivateAtrr

        obj1 = MyClass()
        print(obj1.myGetter() )
        obj1.mySetter(“new value of the private attr”)

    we can also reach the private attributes of the class in general (not for an instance of it) by typing the name of the class after and underscore (_) followed by double underscore (__) and the name of the attribute (no spaces) :
print( _MyClass__myPrivateAtrr )

---

## Class inheritance:

### The child class: 

we can define a class that inherits all the attributes and methods of the parent class (it is like we define the same attributes and methods in the new class with the same values, names, types, scopes and parameters)

    class MyClass:
        x = 50
        def func(self, y)
            return self.x + y

    class myChild(myClass):
        pass

    obj1 = myChild()
    print(obj1.x)
    obj1.func(20)

### Overwriting: 

when we redefine an attribute or a method or a constructor of a parent class inside his child class, we overwrite those to have new values only for the child

    class MyClass:
        def __init__(self, a, b):
            print(a, b)
        x = “parent value”
        def func(self, y)
            return self.x + y

    class myChild(myClass):
        x = “child value”
        def func(self, y, z)
            return self.x + y + z

    obj1 = myChild(3, 4)
    print(obj1.x)
    obj1.func(20, 30)

### The “init” keyword:

to keep the inheritance of the parent's (init) function, add a call to the parent's (init) function:

    class myChild(myClass):
        def __init__(self, a, b):
            myClass.__init__(self, a, b)

### The “super” keyword:

we can force the child to inherit all the attributes and properties of his parent even if we overwrite

    class myChild(myClass):
        def __init__(self, a, b):
            super().__init__()

---

## Magic methods:

they are a special set of available methods we can define in a class so that we can specify a the behavior of the class whenever we use a specific operator

Example:

if we use the ( + ) operator between two instances of the class (MyClass), the function (__add__) will be called, every magic method has to have a parameter called (other) besides the (self) parameter, we pass the whole instance as an argument for the (other) parameter

    class MyClass:
        def __init__(self, par1, par2)
            self.x = par1
            self.y = par2
        def __add__(self, other):
            return MyClass( self.x + other.x,  self.y + other.y )

    first = MyClass(5, 7)     #the instance (first) has x=5, y=7
    second = MyClass(3, 9)    #the instance (second) has x=3, y=9
    result = first + second
    print(result.x)           #it prints 8 which is (5+7)
    print(result.y)           #it prints 12 which is (3+9)

the instance (result) invoked the (__add__) function only without even the constructor (__init__), the (self) parameter here will take the argument that is before the ( + ) operator which is (first), and the (other) parameter here will take the argument that is before the ( + ) operator which is (second), so now we can reach the attribute (x) for (first) by (self.x), and for (second) by (other.x)
therefore, the (result) will get the return value which is another calling that will make it get x=5+3, y=7+9
so that ( first + second ) is translated into ( first.__add__(second) )

---