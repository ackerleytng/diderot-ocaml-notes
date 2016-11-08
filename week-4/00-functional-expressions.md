# Functional Expressions

Functional Expressions in OCaml

+ Syntax: `function id -> exp`
+ Function taking one argument `id` and returning the value of expression `exp`
+ Example: `function x -> x + 1`
+ Scope of `id` is restricted to `exp`
+ Type: `t1 -> t2` where
    + `t1` is the type of `id`
    + `t2` is the type of `exp`

Defining functions

```
let f x = e
```

is just an abbreviation for 

```
let f = function x -> e
```

How this maps to pattern matching

+ The general form of a function definition is

```
function
  | pattern_1 -> expression_1
  ...
  | pattern_n -> expression_n
```

The form `function x -> exp` is just a special case

Example

```
let rec length = function
  | [] -> 0
  | _ :: r -> 1 + length r
```

```
type expr =
  | Int of int
  | Add of expr * expr
  
let rec eval = function 
  | Int n -> n
  | Add (e1, e2) -> (eval e1) + (eval e2)
```
