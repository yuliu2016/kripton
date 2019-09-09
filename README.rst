============================
Kripton Programming Language
============================

Kripton is a conceptual programming language design,
inspired by Kotlin and Python.

Examples
========

Generate a list of prime numbers under a maximum:

.. code-block:: ruby

    prime_list = def(max: int) -> list<int> {
        return (2:max).filter { p ->
            not (2:sqrt(n)).any: q -> p % q == 0
        }
    }
