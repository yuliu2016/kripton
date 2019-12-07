============================
Kripton Programming Language
============================

Kripton is a conceptual programming language design,
inspired by Kotlin and Python. It includes imperative,
functional, and object-oriented coding styles and
supports both dynamic and static typing

Simple Code Examples
====================

Printing stuff:

.. code-block:: python

    message = "Hello World"
    print(f"The Message is {message}")
    print("The Message is ", message)
    print("The Message is {}".template().format(message))

Loops:

.. code-block:: ruby

    repeat(10) {
        print("Repeating")
    }

    for i in [0:100] {
        print(f"The square of {i} is {i * i}")
    }

    f = file("toRead.txt")
    while not f.eof() {
        print(f.readline())
    }

Data structures:

.. code-block:: python

    numbers = [1,2,3]
    numbers.append("not the same type")
    fruit_to_colour = {
        "apple": "red",
        "banana": "yellow",
        "orange": "orange"
    }

Function definitions, sequences, and functional programming:

.. code-block:: ruby

    prime_sequence = def(max: int) -> sequence<int> {
        return [2:max].|filter { p => 
            not [2:sqrt(n)].|any { q => p % q == 0 }
        }
    }

Pipe Call Functions:

.. code-block:: ruby

    sum = def(x) {
        s = 0
        for item in x {
            s += item
        }
        return s
    }

    x = [1,3,5,7].|sum()
    print(x)


Function Parameter Destructuring:

.. code-block:: ruby

    map = def(collection, func) {
        result = []
        for item in collection {
            result.append(func(item))
        }
        return results
    } 

    # All are valid
    squared = [1:100].|map { v => v * v }
    squared = [1:100].|map(v => v * v)
    squared = map([1:100], v => v * v)
    squared = map([1:100]){ v => v * v }

    print(squared)

Data Classes:

.. code-block:: ruby

    Rect = class(w, h) 
    Rect.|area = self => self.w * self.h
    Rect.|perim = self => 2 * (self.w + self.h)
    
Documentation:

.. code-block:: kotlin

    /**
     * This is a docstring. Reference any symbols like [int] or [list::append]
     */
     a = 123

Full Examples
=============

Number Guessing Game
--------------------

.. code-block:: ruby

    from random import choose_random

    n = [1:100].|choose_random()

    while True {
        try: guess = input("Enter your guess: ").|int()
        except FormatError: continue

        when {
            guess < n: print("Too Small")
            guess > n: print("Too big")
            else: break
        }
    }

    print("Correct!!")