# Expressions

+ Expressions compute values

+ `if ... then ... else`
+ Expression has to have a type, so the types of the expressions in `then` and `else` must be the same
+ Language allows a missing `else` expression, but this is not what you expect it to be

Functions

+ function application:
    + `f expression ... expression`
+ functions can be under-supplied with arguments

Polymorphic Operators

+ Operators have an infix syntax
+ Operators also have a type: `+ : int -> int -> int`
+ Some have polymorphic type: `> : 'a -> 'a -> bool`
    + `'a` is read with their greek pronunciation (alpha)
    + Can be instantiated with any type
