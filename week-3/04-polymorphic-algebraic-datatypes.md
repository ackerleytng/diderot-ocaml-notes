# Polymorphic Algebraic Datatypes

Type parametric programming

+ `list` is a type constructor parameterized by the type of the elements
+ Most of the functions over lists do no depend on the type of the elements
+ Hence, the module `List` contains only polymorphic functions
+ These are written once and for all, maximizing code reuse

A programmer can define his/her own parameterized types

The `option` type is predefined

```
type 'a option =
  | None
  | Some of 'a
```

For example: a generic binary search tree

```
type 'a bst =
  | Empty
  | Node of 'a bst * 'a * 'a bst

let rec find_max = function
  | Empty -> assert false
  | Node (_, x, Empty) -> x
  | Node (_, x, r) -> find_max r

let rec insert x = function
  | Empty -> Node (Empty, x, Empty)
  | Node (l, y, r) ->
     if x = y then Node (l, y, r)
     else if x < y then Node (insert x l, y, r)
     else Node (l, y, insert x r)

let rec delete x = function
  | Empty -> Empty
  | Node (l, y, r) ->
     if x = y then join l r
     else if x < y then Node (delete x l, y, r)
     else Node (l, y, delete x r)
and join l r =
  match l, r with 
  | Empty, r -> r
  | l, Empty -> l
  | l, r -> let m = find_max l in
            Node (delete m l, m, r)  
```

Syntax

+ To declare a parameterized type

```
type ('a1, ..., 'aN) some_type_identifier = some_type
```

+ The type variables `('a1, ..., 'aN)`
    + represent unknown types
    + can appear in `some_type`
    
+ To instantiate a parameterized type, we write:

```
(some_type, ..., some_type) some_type_identifier
```


