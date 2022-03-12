# Reading: Class 06 :

> [Back to the main](../../README.md)

---

## Importing whatever classes we want

    From random import *

---

## Random features
   
    myList = [1,5,8,9,23,9,7,8,91,2,5,9,94,8,5]

a sample list

    random() 

returns random number between 0 and 1

    randint(1, 6)
    
it will choose a number randomly between 1 to 6

    choice(myList) 
    
it will choose an element randomly from the list 

    choices(myList, k=10)
    
it will choose 10 element randomly from the list with equal probability

    sample(myList, k=10)  
    
it will choose 10 unique element randomly from the list

    sample([“red”, “blue”], counts=[4, 2], k=3)  

it will duplicate the samples with the corresponding samples, and choose 3 unique element randomly from this list:
[“red”, “red”, “red”, “red”, “blue” , “blue”]

    shuffle(myList) 
    
it will shuffle (change positions) of the elements in the list

    randrange(6) 
    
returns random integer from 0 to 6 

    randrange(0, 100, 2) 
    
returns random integer from 0 to 100 but with taking steps of 2 so we have the available list : (0, 2, 4, 6, …)

    gauss(5, 20) 
    
generates a Gaussian distribution float number, (5) is the mean (mu), (20) is the standard deviation (sigma)

--- 

## System Random

    obj = SystemRandom() 
    
create a system random object

    obj.getrandbits(2) 
    
generate a random integer which its binary value consists of (2) digits
so the list we have is : [0, 1, 2 ,3] 
because their corresponding binary values are : [00, 01, 10, 11] all of which consists of 2 binary digits

    obj.randbytes(3) : 
    
generates 3 random bytes, such as: 

b'0i)'

b'\x0f\xb7\xda'

