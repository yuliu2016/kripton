============================
Kripton Programming Language
============================

Kripton is a conceptual programming language design,
inspired by Kotlin and Python.

Features and Design Principles:

- Imperative, functional, and object-oriented
- First-class objects for everything
- Encourages functional style
- Encourages type extensions
- Encourages protected scopes
- Dynamic or static typing

Code Examples
=============

Generate a sequence of prime numbers under a maximum:

.. code-block:: ruby

    prime_sequence = def(max: int) -> sequence<int> {
        return (2:max).filter { p ->
            not (2:sqrt(n)).any: |q| p % q == 0
        }
    }

Number Guessing Game:

.. code-block:: ruby

    import rand.*

    n = (1:100).rand_choice()

    while True {
        try: guess = input("Enter your guess: ").int()
        except FormatError: continue

        when {
            guess < n -> print("Too Small")
            guess > n -> print("Too big")
            else -> break
        }
    }

    print("Correct!!")

Data Classes (and generic templates):

.. code-block:: ruby

    Rect = dataclass<T: number>(w: T, h: T)

    Rect::area = def(self) {
        return self.w * self.h
    }

    Rect::perim = def(self) {
        return 2 * (self.w + self.h)
    }

Data structures:

.. code-block:: python

    numbers = [1,2,3]
    fruit_to_colour = {
        "apple": "red",
        "banana": "yellow",
        "orange": "orange"
    }
    array_number = arange(1:100:2)
    equal_array = linspace(1:40, 13)