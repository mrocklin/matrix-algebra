Matrix Algebra
==============

An algebra for Matrix Expressions written in Maude. 

Code
====

`algebra.maude`
---------------

defines an algebra for matrix expressions, i.e.

> `transpose(Y X) Y + A B`

This language includes multiplies, adds, backsolves, transposes, and inverses

`assumptions.maude`
-------------------

defines rules for predicates like

> `X is symmetric , Y is orthogonal`

We group these predicates into contexts (here called Facts) and declares rules
like the following

> `ceq Facts => X Y is invertible = true if Facts => X is invertible  
>                                       and Facts => Y is invertible .`

We include predicates like symmetric, orthogonal, invertible, singular,
positive-definite, triangular, diagonal, etc.... 
If you are interested it is very easy to add more. The existing code should
provide enough examples.

`simplify.maude`
----------------

combines these two and includes simplififcation rules like 

> `ceq simplify(X transpose(X) with Facts) = I with Facts if Facts => X is orthogonal .`

Other than a few maude keywords (like `ceq`) this code is intended to look like
mathematical statements. This allows for easy extensibility (you can contribute
to this project without knowing maude) and for easy verifiability (the code is 
clear.)

`simplify-sys.maude` contains simplification rules that include branching
paths. I.e. for `X Y Z` there are two ways in which we could group terms
`(X Y) Z` or `X (Y Z)`. This requires a search mechanism rather than 
straightforward equational rewriting.

> `rl [right] : simplify(X (Y Z) with C) => simplify(X with C) simplify(Y Z with C) .`

> `rl [left]  : simplify(X (Y Z) with C) => simplify(X Y with C) simplify(Z with C) .`

As a result of all of this we can perform simplifications like the following 

Example
-------
> `simplify(transpose(Y X) Y + A B with X is symmetric , Y is orthogonal)`

reduces to

> `X + A B with X is symmetric, Y is orthogonal`

Tests
-----

The `src/tests` directory contains a number of examples that are used to verify
the correctness of this code. It is a good place to start. 

After you have maude installed you may run the tests as follows

> `maude src/tests/*.maude`

Install
=======

You can clone this repository with 

    $ git clone git://github.com/mrocklin/matrix-algebra.git

You will need the Maude system

[http://maude.cs.uiuc.edu/](http://maude.cs.uiuc.edu/)

Which is available by apt using 

    $ sudo apt-get install maude

Author
======

[Matthew Rocklin](http://matthewrocklin.com/)
