# Constructing and Observing Tuples

+ The type constructor `*` constructs tuple types

```
some_type * ... * some_type
```

+ A tuple is constructed by separating its components with a comma

```
(some_expression, ..., some_expression)
```

Pattern matching

+ Patterns describe how values are observed by the program
+ Use `_` to ignore values using a wildcard pattern

```
let (x, _) = (6 * 3, 2) in x
```

+ A pattern that matches a tuple has the form 

```
(some_pattern, ..., some_pattern)
```

+ The number of subpatterns must equal to the number of tuple components
+ An identifier can only occur once in a pattern

Implementation in the machine

+ A tuple is represented by a heap-allocated block
+ The program holds a pointer to this block
+ This pointer can be shared

Structural equalty vs physical equality

+ `=` implements structural equality
+ Two values are structurally equal if they have the same content
+ `==` implements physical equality
+ Two values are physically equal if they are stored in the same memory location

Ill-formed patterns

+ Invalid arity

```
let (x, _) = (1, 2, 3);;
```

+ Nonlinear patterns

```
let (x, x, y) = (1, 2, 3);;
```

