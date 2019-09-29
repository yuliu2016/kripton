===============
Kripton Grammar
===============

This document describes Kripton's Grammar. Mostly copied from Python's Grammar

All Tokens
=========

.. code-block::

    ENDMARKER
    NAME
    NUMBER
    STRING
    NEWLINE

    LPAR                    '('
    RPAR                    ')'
    LSQB                    '['
    RSQB                    ']'
    COLON                   ':'
    COMMA                   ','
    SEMI                    ';'
    PLUS                    '+'
    MINUS                   '-'
    STAR                    '*'
    SLASH                   '/'
    VBAR                    '|'
    AMPER                   '&'
    LESS                    '<'
    GREATER                 '>'
    EQUAL                   '='
    DOT                     '.'
    PERCENT                 '%'
    LBRACE                  '{'
    RBRACE                  '}'
    EQEQUAL                 '=='
    NOTEQUAL                '!='
    LESSEQUAL               '<='
    GREATEREQUAL            '>='
    TILDE                   '~'
    CIRCUMFLEX              '^'
    LEFTSHIFT               '<<'
    RIGHTSHIFT              '>>'
    DOUBLESTAR              '**'
    PLUSEQUAL               '+='
    MINEQUAL                '-='
    STAREQUAL               '*='
    SLASHEQUAL              '/='
    PERCENTEQUAL            '%='
    AMPEREQUAL              '&='
    VBAREQUAL               '|='
    CIRCUMFLEXEQUAL         '^='
    LEFTSHIFTEQUAL          '<<='
    RIGHTSHIFTEQUAL         '>>='
    DOUBLESTAREQUAL         '**='
    DOUBLESLASH             '//'
    DOUBLESLASHEQUAL        '//='
    AT                      '@'
    ATEQUAL                 '@='
    RARROW                  '->'
    ELLIPSIS                '...'
    COLONEQUAL              ':='

    OP
    AWAIT
    ASYNC
    TYPE_IGNORE
    TYPE_COMMENT
    ERRORTOKEN

Misc Definitions
================

.. code-block:: ebnf

    dotted_name: NAME ('.' NAME)*
    


Statements
==========

.. code-block:: ebnf

    # Single word statements
    past_stmt: 'pass'
    break_stmt: 'break'
    continue_stmt: 'continue'

    # Import Statements

    import_as_name: NAME ['as' NAME]
    import_as_names: import_as_name (',' import_as_name)* [',']
    dotted_as_name: dotted_name ['as' NAME]
    dotted_as_names: dotted_as_name (',' dotted_as_name)*
    
    import_name: 'import' dotted_as_names
    import_from: ('from' (('.' | '...')* dotted_name | ('.' | '...')+)
              'import' ('*' | '(' import_as_names ')' | import_as_names))
    import_stmt: import_name | import_from


    assert_stmt: 'assert' test [',' test]
    
    
            