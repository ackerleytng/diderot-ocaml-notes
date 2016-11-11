# Exceptions

Exceptions can be used to signal and handle exceptional conditions

+ Exceptions are constructors of a special sum type `exn`
+ These constructors can have arguments, like all other constructors
+ New exceptions can be defined at any time
+ The `exn` can be extended
+ Exceptions cannot be polymorphic
+ Raising and handling exceptions is very fast

Declare exceptions using the `exception` keyword.

```
exception E
```

Signal exceptions using the `raise` keyword

```
raise E
```

Example: head of an empty list

```
exception Empty_list

let head = function
    [] -> raise Empty_list
  | a :: r -> a 
```

Handling exceptions

```
try
   e
with
    p1 -> e1
  | p2 -> e2
  | ...
```

+ Evaluate `e`, then if `E` is raised, match it with the patterns in the `with` clause
+ You can match the exception with any pattern of the type `exn`
+ If `E` matches pattern `pi`, evaluate expression `ei`
+ All the `ei` must have the same type as `e`

Example: use exceptions to return as soon as we see a zero

```
let multlexc l =
  let rec aux = function
      [] -> 1
    | a :: rest -> if a = 0 then raise Zero else a * (aux rest)
  in
  try aux l with Zero -> 0
```

Runtime errors can be captured as exceptions, such as

+ Division by zero
+ Incomplete pattern matching
+ Out-of-bound access to indexed data structures like arrays
