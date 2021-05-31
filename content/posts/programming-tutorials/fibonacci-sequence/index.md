---
title: "Fibonacci Sequence"
description: "Tutorial for printing the Fibonacci sequence"
date: 2021-06-01T00:12:25+08:00
hero: images/pexels-flash-dantz-7658151.jpg
menu:
  sidebar:
    name: "Fibonacci Sequence"
    identifier: fibonacci-sequence
    parent: programming-tutorials
#draft: true
---

The Fibonacci sequence is a series of numbers where a number is the addition
of the last two numbers. This is one of the basic forms of exercise used in
programming is almost always present in a programming exam. Therefore, learning
how to print the Fibonacci sequence is essential to anyone learning programming
or a new programming language.

```
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377
```

Typically, there are two implementations of the Fibonacci sequence - (1) the
iterative algorithm and (2) the recursive algorithm. 

I have written here both iterative and recursive implementations. For each implementation, I've also written both the ascending order and the descending (reverse) order implementations.


## Iterative Implementation
Iteration is when a sequence of instructions is repeatedly executed until a
certain condition is met.

### Ascending Order

```python
def fibonacci(terms):
    """Return a Fibonacci sequence for the given number of terms."""
    if terms < 1:
        return []
    sequence = [0]
    count = 1
    prev = 0
    num = 1
    while count < terms:
        sequence.append(num)
        temp = num
        num = prev + temp
        prev = temp
        count += 1
    return sequence

terms = int(input("Enter the number of terms: "))
for num in fibonacci(terms):
    print(num, end=" ")
# This will add a line break after printing the sequence
print("")
```

### Descending Order

```python
def fibonacci(terms):
    """Return a Fibonacci sequence for the given number of terms."""
    if terms < 1:
        return []
    sequence = [0]
    count = 1
    prev = 0
    num = 1
    while count < terms:
        sequence.append(num)
        temp = num
        num = prev + temp
        prev = temp
        count += 1
    return sequence

terms = int(input("Enter the number of terms: "))
# Simply use the built-in reversed() function in Python to traverse the list
# in reverse order.
for num in reversed(fibonacci(terms)):
    print(num, end=" ")
# This will add a line break after printing the sequence
print("")
```

## Recursive Implementation
Recursion is a method of solving a problem where the solution depends on
solutions to smaller instances of the same problem. Most computer programming 
languages support recursion by allowing a function to call itself from within 
its own code.

### Ascending Order
This is the common recursive implementation of printing a Fibonacci sequence.
However, if you look closely, we're still using a for loop in the driver code.
The actual recursive implementation here is the fibonacci() function which
returns the nth term in the sequence.

```python
def fibonacci(n):
    """Return the nth term in a Fibonacci sequence."""
    if n <= 1:
       return n
    else:
       return (fibonacci(n-1) + fibonacci(n-2))

terms = int(input("Enter the number of terms: "))
for n in range(terms):
    print(fibonacci(n), end=" ")
# This will add a line break after printing the sequence
print("")
```


### Descending Order

```python
def fibonacci(n):
    """Return the nth term in a Fibonacci sequence."""
    if n <= 1:
       return n
    else:
       return (fibonacci(n-1) + fibonacci(n-2))

terms = int(input("Enter the number of terms: "))
# Simply use the built-in reversed() function in Python to traverse the list
# in reverse order.
for n in reversed(range(terms)):
    print(fibonacci(n), end=" ")
# This will add a line break after printing the sequence
print("")
```
