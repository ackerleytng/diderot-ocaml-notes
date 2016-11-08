# Advanced Topics

Precise typing

+ A sum type with only one constructor can be useful to discriminate between two types that are structurally equivalent but semantically different

Example: currencies

```
type euro = Euro of float

type dollar = Dollar of float

let euro_of_dollar (Dollar d) = Euro (d /. 1.33)

let x = Dollar 4.

let y = Euro 5.

let valid_comparison = (euro_of_dollar x < y)
```

Disjunctive patterns

+ Sometimes, the same code is duplicated in several branches
+ or-patterns allow factorization of these branches into a unique branch
+ `some_pattern_1 | some_pattern_2` corresponds to the observation of `some_pattern_1` or `some_pattern_2`
+ `some_pattern_1` and `some_pattern_2` must contain the same identifiers
+ The following are the same:

```
let remove_zero_or_one_head = function
  | 0 :: xs -> xs
  | 1 :: xs -> xs
  | l -> l

let remove_zero_or_one_head = function
  | 0 :: xs | 1 :: xs -> xs
  | l -> l

let remove_zero_or_one_head = function
  | (0 | 1) :: xs -> xs
  | l -> l
```

as-patterns

+ A matched component could be named
+ `some_pattern as x` is read as "If the value can be observed using `some_pattern`, name it `x`

Example:

```
let rec duplicate_head_at_the_end = function
  | [] -> []
  | (x :: _) as l -> l @ [x]
```

Constrained pattern matching using `when`

+ A boolean expression, called a guard, can add an extra constraint to a pattern
+ This guard is introduced by the keyword `when`

Example:

```
let rec push_max_at_the_end = function
  | ([] | [_]) as l -> l
  | x :: ((y :: _) as l) when x <= y -> x :: push_max_at_the_end l
  | x :: y :: ys -> y :: push_max_at_the_end (x :: ys)
```


