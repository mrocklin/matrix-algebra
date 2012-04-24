Matrix Algebra
==============

An algebra for Matrix Expressions written in Maude. 

The module defines an algebra of matrix expressions i.e.

transpose(Y X) Y + A B

It also defines a logical framework for known facts about these expressions i.e.

X is symmetric, Y is orthogonal

With these two modules we can specify simplification rules like

M transpose(M) = Identity if M is orthogonal

Which allows us to simplify matrix expressions given known facts

This algebra and these rules are written in the Maude System, a language for 
specifying other small languages that handles computation through rewrite 
rules. As a result much of the code is intended to read like mathematical
statements.

Author
======
Matthew Rocklin
