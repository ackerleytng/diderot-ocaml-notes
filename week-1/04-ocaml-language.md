# Bird's eye view of the OCaml language

+ Safety from strong static typing and pattern matching
+ Conciseness from polymorphic typing and type inference
+ Expressiveness from higher order functions

In OCaml, lists are built-in

+ `[]` is the empty list
+ `a::l` is a list with `a` as the first element and `l` as the rest of the list

```
let rec suml = 
function 
  [] -> 0
| a::rest -> a + (sum1 rest);;
```

The above can be generalised

```
let rec fold op e = 
function
  [] -> e
| a::rest -> op a (fold op e rest);;
```

`^` is the concatenation operator

Pattern matching: ensuring that all cases are handled

```
let rec destutter =
function
  | [] -> []
  | x :: [] -> x :: []
  | x :: y :: rest ->
     if x = y then destutter (y :: rest)
     else x :: destutter (y :: rest) ;;
```
