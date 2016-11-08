# Functions as First-Class Values

Functions are Values

+ Expressions may denote integers, booleans, ..., or functions
+ Functions are just values of another type
+ Types govern function application: We can apply `e1` to `e2` when
    + `e1` has a type `t1 -> t2`
    + `t1` matches the type of `e2`
+ Functions may, like other values,
    + be part of a structured data value, like a list
    + be actual arguments of functions
    + be the result value of a function application

Example

```
let fl = [(function x -> x + 1);(function x -> 2 * x)]

(List.hd fl) 17
(* gives 18 *)

let apply_twice f x = f (f x)

apply_twice (function x -> 2 * x) 1
(* gives 4 *)

let rec apply_n_times f n x =
  if n <= 0
  then x
  else apply_n_times f (n - 1) (f x)
  
apply_n_times (function x -> 2 * x) 10 1
(* gives 1024 *)

let compose f g -> (function x -> f (g x))

(compose (function x -> x + 1) (function x -> 2 * x)) 10
(* gives 21 *)
```

+ Function application associates to the left

```
exp1 exp2 exp3
```

is equivalent to

```
(exp1 exp2) exp3
```
