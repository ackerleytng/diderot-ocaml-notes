# Recursive Types

Deep data structures

+ Some data structures like lists and trees have an unbounded depth
+ For example, a list of integers is either
    + An empty list or
    + An integer and the rest of the list
+ "The rest of the list" is also a list

For example,

```
type int_list =
  | EmptyList
  | SomeElement of int * int_list
```

Implementation in the machine


```
SomeElement (1, SomeElement (3, EmptyList))
```

implements a linked list data structure

Recursive types

+ A sum type can refer to itself in its own definition
+ Such a sum type is therefore recursive
+ Functions over a recursive type are often defined by case analysis and recursion

```
let rec length = function
  | EmptyList -> 0
  | SomeElement (x, 1) -> 1 + length 1
```

Lists

+ The type for lists of elements of type t is predefined in OCaml
+ The empty list is `[]`
+ `::` corresponds to `SomeElement`


Reverse in quadratic time

```
(* The '@' is a predefined operator that appends a list to another one. *) 
let rec rev = function
    [] -> []
  | x :: xs -> rev xs @ [ x ]
```

Reverse in linear time

```
let rec rev_aux accu = function
    [] -> accu
  | x :: xs -> rev_aux (x :: accu) xs
```

Another example

```
let rec uniq = function 
    [] -> []
  | [x] -> [x]
  | x :: x' :: xs ->
    if x = x' then uniq (x' :: xs)
    else
      x :: uniq (x' :: xs)
```
