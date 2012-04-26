Matrix Algebra
==============

An algebra for Matrix Expressions written in Maude. 

The module defines an algebra of matrix expressions i.e.

transpose(Y X) Y + A B

It also defines a logical framework for known facts about these expressions i.e.

X is symmetric , Y is orthogonal

With these two modules we can specify simplification rules like

M transpose(M) = I if M is orthogonal

Which allows us to simplify matrix expressions given known facts. For example
the expression

simplify(transpose(Y X) Y with X is symmetric , Y is orthogonal)
reduces to
X

This algebra and these rules are written in the Maude System, a language for 
specifying other small languages that handles computation through rewrite 
rules. As a result much of the code is intended to read like mathematical
statements. The expressions above are valid statements.

As a disclaimer the equations are not currently confluent. This means that the
results are dependent on the order in which the equations are applied which, in
general, is not structured.

Author
======
Matthew Rocklin

To Run
======

Install the maude system. This can be done on debian/ubuntu systems using
apt-get install maude

Run the tests using 
maude src/tests/*.maude
