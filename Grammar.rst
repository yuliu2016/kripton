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

Atoms and Expressions
=====================

This section outlines the operator precedence

.. code-block:: ebnf

    testlist_comp: (namedexpr_test|star_expr) ( comp_for | 
        (',' (namedexpr_test|star_expr))* [','] )
    atom: ('(' [yield_expr|testlist_comp] ')' |
       '[' [testlist_comp] ']' |
       '{' [dictorsetmaker] '}' |
       NAME | NUMBER | STRING+ | '...' | 'None' | 'True' | 'False')
    trailer: '(' [arglist] ')' | '[' subscriptlist ']' | '.' NAME

    atom_expr: [AWAIT] atom trailer*
    power: atom_expr ['**' factor]
    factor: ('+'|'-'|'~') factor | power
    term: factor (('*'|'@'|'/'|'%'|'//') factor)*
    arith_expr: term (('+'|'-') term)*
    shift_expr: arith_expr (('<<'|'>>') arith_expr)*
    and_expr: shift_expr ('&' shift_expr)*
    xor_expr: and_expr ('^' and_expr)*

    expr: xor_expr ('|' xor_expr)*


Boolean Expressions:

.. code-block:: ebnf

    comp_op: '<'|'>'|'=='|'>='|'<='|'<>'|'!='|'in'|'not' 'in'|'is'|'is' 'not'
    comparison: expr (comp_op expr)*
    not_test: 'not' not_test | comparison
    and_test: not_test ('and' not_test)*
    or_test: and_test ('or' and_test)*
    lambdef: 'lambda' [varargslist] ':' test
    test: or_test ['if' or_test 'else' test] | lambdef


Simple Statements
=================

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
    
    small_stmt: (expr_stmt | del_stmt | pass_stmt | flow_stmt |
             import_stmt | global_stmt | nonlocal_stmt | assert_stmt)
    simple_stmt: small_stmt (';' small_stmt)* [';'] NEWLINE


Compound Statements
===================

.. code-block:: ebnf

    with_item: test ['as' expr]
    with_stmt: 'with' with_item (',' with_item)*  ':' [TYPE_COMMENT] suite

    try_stmt: ('try' ':' suite
           ((except_clause ':' suite)+
            ['else' ':' suite]
            ['finally' ':' suite] |
           'finally' ':' suite))

    compound_stmt: if_stmt | while_stmt | for_stmt | try_stmt | with_stmt | funcdef | classdef | decorated | async_stmt

    stmt: simple_stmt | compound_stmt
            