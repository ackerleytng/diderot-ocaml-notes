# Recursion

+ Functions that are defined by calling themselves on smaller arguments
+ Define a recursive function using `rec`, otherwise OCaml will think you're referring to the previous value of `f` or whatever the function/variable was previously named

Example

```
let rec fact n = if n <= 1 then 1 else n * fact (n-1);;
```

Mutually Recursive Functions
+ Generalization of direct recursion
+ Several functions are defined by calling each other on smaller arguments

Example

```
let rec even x = if x = 0 then true else odd (x - 1)
and odd x = if x = 0 then false else even (x - 1)
```
