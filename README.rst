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
        return [2:max].filter { p =>
            not [2:sqrt(n)].any(q => p % q == 0)
        }
    }

Data Classes:

.. code-block:: ruby

    Rect = dataclass(w, h)

    Rect.area = def(self) {
        return self.w * self.h
    }

    Rect.perim = def(self) {
        return 2 * (self.w + self.h)
    }
    
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

    from random import *

    n = [1:100].rand_choice() # choose a random number between 1 and 100

    while True {
        try: guess = input("Enter your guess: ").int()
        except FormatError: continue

        when {
            guess < n: print("Too Small")
            guess > n: print("Too big")
            else: break
        }
    }

    print("Correct!!")

Connect Four Game
-----------------

.. code-block:: ruby

    Cell = enum(empty=0, red=1, yellow=2)
    Players = enum(red=1, yellow=2)

    state = object(
        board = array<T=int>(shape=(7,6), fill=Cell.empty.value),
        player = players.red
    )

    state.print_board = def() {
        for row in [:board.len] {
            for col in [:row.len] {
                state = Cell(board[row, col])
                ch = when state {
                    Cell.empty: "."
                    Cell.red: "X"
                    Cell.yellow: "O"
                }
                print(ch, end=" ")
            }
            print()
        }
    }

    state.next_player = def() {
        player = when player {
            Players.red: Players.yellow
            Players.yellow: Players.red
        }
    }

    get_move = def() -> int {
        while True {
            try: return input("Enter column to play: ").int()
            except FormatError:
                print("Invalid Input")
        }
    }

    while True {
        
    }