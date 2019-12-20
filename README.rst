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

    f = open("toRead.txt")
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
    set_example = {1, 2, 3}

Function definitions, sequences, and functional programming:

.. code-block:: ruby

    import math
    prime_sequence = def(max) {
        return [2:max] | filter { p => 
            [2:math.sqrt(p)] | all { q => p % q != 0 }
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

    x = [1,3,5,7] | sum()
    print(x)


Function Parameter Destructuring:

.. code-block:: ruby

    map = def(collection, ^func) {
        result = []
        for item in collection {
            result.append(func(item))
        }
        return results
    } 

    # All are valid
    squared = [1:100] | map { v => v * v }
    squared = [1:100] | map(v => v * v)
    squared = map([1:100]) { v => v * v }
    squared = map([1:100], v => v * v)

    print(squared)

Data Classes:

.. code-block:: ruby

    Rect = class(w, h) {
        area = self => self.w * self.h
        perim = self => 2 * (self.w + self.h)
    }

    xyz = Rect(1, 2)
    print(xyz.area())
    
Documentation:

.. code-block:: kotlin

    /**
     * This is a docstring. Reference any symbols like [int] or [list::append]
     */
     a = 123

Operator Precedence:

.. code-block:: python

    # 1. def(){}, x => y
    # 2. if condition {} else {}
    # 3. condition ? val-true : val-false
    # or
    # and
    # not x
    # in, not in, is, is not, <, <=, >, >=, !=, ==
    # &
    # | (pipe)
    # || (bitwise or)
    # ^^ (bitwise xor)
    # && (bitwise and)
    # <<, >>
    # +, -
    # *, /, %
    # +x, -x, ~x
    # **
    # x[y], x[y:z], x(y), x.y
    # (...), [...], {k:v}, {...} 

Full Examples
=============

Number Guessing Game
--------------------

.. code-block:: ruby

    from random import choose_random

    n = [1:100] | choose_random()

    while True {
        try: guess = input("Enter your guess: ") | int()
        except FormatError: continue

        if guess < n {
            print("Too Small")
        } elif guess > n {
            print("Too Big")
        } else: break
    }

    print("Correct!!")