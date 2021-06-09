---
title: "Factorial"
description: "Tutorial for calculating the factorial"
date: 2021-06-01T02:57:52+08:00
menu:
  sidebar:
    name: "Factorial"
    identifier: factorial
    parent: programming-tutorials
---

Factorial is the product of all positive integers less than or equal to a given
positive integer and denoted by that integer and an exclamation point. 

```
n! = n * (n-1) * (n-2) * (n-3) ... 3 * 2 * 1
```

For example

```
5! = 5 * 4 * 3 * 2 * 1 = 120
```

Just like the Fibonacci sequence, this is one of the basic forms of exercise 
used in programming and is commonly used to introduce recursion. I have written 
here both iterative and recursive implementations. 


## Iterative Implementation
Iteration is when a sequence of instructions is repeatedly executed until a
certain condition is met.

```python
def factorial(n):
    """Return the factorial of a given number."""
    # Take note that 0! = 1
    if n == 0:
        return 1
    result = 1
    while (n > 0):
        result = result * n
        n -= 1
    return result

n = int(input("Enter a positive integer: "))
if n < 0:
    print("Must enter a positive integer.")
    exit(1)
print(factorial(n))
```

## Recursive Implementation
Recursion is a method of solving a problem where the solution depends on
solutions to smaller instances of the same problem. Most computer programming 
languages support recursion by allowing a function to call itself from within 
its own code.

```python
def factorial(n):
    """Return the factorial of a given number."""
    # Take note that 0! = 1
    if n == 0:
        return 1
    return n * factorial(n - 1)

n = int(input("Enter a positive integer: "))
if n < 0:
    print("Must enter a positive integer.")
    exit(1)
print(factorial(n))
```

You can see in this implementation that it is much shorter than the iterative
implementation and it factorial function calls itself.
