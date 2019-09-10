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

Generate a list of prime numbers under a maximum:

.. code-block:: ruby

    prime_list = def(max: int) -> list<int> {
        return (2:max).filter { p ->
            not (2:sqrt(n)).any: q -> p % q == 0
        }
    }

Number Guessing Game:

.. code-block:: ruby

    import rand.*

    n = (1:100).rand_choice()

    while True {
        guess = input("Enter your guess: ").int()

        when {
            guess < n -> print("Too Small")
            guess > n -> print("Too big")
            else -> break
        }
    }

    print("Correct!!")