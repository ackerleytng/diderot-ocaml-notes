# Folding Functions on Lists

Introduction

+ Mapping: each element of a list is considered in isolation
+ Folding is about combining all elements of a list using a binary operator

+ Folding Right: `List.fold_right` is combining from the right
    + `List.fold_right list value`

```
let rec fold_right f l b = match l with
  | [] -> b
  | h :: r -> f h (fold_right f r b)
```

+ Folding Left: `List.fold_left` is combining from the left
    + `List.fold_left value list`

```
let rec fold_left f b = function
  | [] -> b
  | h :: r -> fold_left f (f b h) r
```

Example: Inner product of integer vectors

```
let product v1 v2 =
  List.fold_left (+) 0 (List.map2 ( * ) v1 v2)
```

Example: Counting elements of list

```
let countif p l = List.fold_left
  (fun counter element -> if p element then counter + 1 else counter)
  0
  l
```
