# Basic Data Types

+ Type inference
    + Types of identifiers are inferred, not declared
    + Reconciles the flexibility of untyped languages with the safety of typed languages
    + OCaml has a rich type system and polymorphism gives us more flexibility

+ Basic types
    + `int`: -2^62 ... 2^62 -1
        + Calculations performed modulo 2^63
        + `/` is integer division, remainder is `mod`
    + `bool`: `true` and `false`
        + `&&`, `||` and `not`
        + `=` for equals, not `==`
        + `<>` for not equals
        + Can only compare values of the same type
    + `float`, `string`, `char`
