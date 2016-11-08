# Functions with Multiple Arguments

Functions in OCaml are actually functions with one argument only; functions with several arguments are just an abbreviation for nested functions with one argument each.

+ An anonymous function with several arguments is written

```
fun p1 ... pn -> exp
```

Where the `pi` are patterns

+ Unlike `function`, the `fun` form only allows one case. (Cannot match multiple cases)

Example

```
let f1 = function n -> (function x -> n + x)

(f1 17) 73
(* gives 90 *)

f1 17 73
(* gives 90, since function application associates to the left *)
```

This is the same as 

```
let f2 = fun n x -> n + x

f2 17 73
(* gives 90 *)

(f2 17) 73
(* also gives 90 *)
```

+ Functions with multiple arguments are the same thing as functions returning functions as values
+ More precisely

```
fun x1 ... xn -> e
```

is just an abbreviation for 

```
function x1 -> ... -> function xn -> e
```

Example

```
type expr =
  | Var of string
  | Add of expr * expr
  
let rec eval = fun environment expr -> match expr with
  | Var x -> List.assoc x environment
  | Add (e1, e2) -> (eval environment e1) + (eval environment e2)
  
eval [("x",2); ("y",5)] (Add (Var "x", Add (Var "x", Var "y")))
(* gives 9 *)

let rec eval = function environment -> function expr -> match expr with
  | Var x -> List.assoc x environment
  | Add (e1, e2) -> (eval environment e1) + (eval environment e2)

eval [("x",2); ("y",5)] (Add (Var "x", Add (Var "x", Var "y")))
(* also gives 9 *)

let rec eval = function environment -> function
  | Var x -> List.assoc x environment
  | Add (e1, e2) -> (eval environment e1) + (eval environment e2)

eval [("x",2); ("y",5)] (Add (Var "x", Add (Var "x", Var "y")))
(* also gives 9 *)

let rec eval environment = function
  | Var x -> List.assoc x environment
  | Add (e1, e2) -> (eval environment e1) + (eval environment e2)

eval [("x",2); ("y",5)] (Add (Var "x", Add (Var "x", Var "y")))
(* also gives 9 *)
```
