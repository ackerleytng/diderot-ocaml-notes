# Tagged Values

OCaml has a sum type to capture the disjoint union of types

For example,

```
type some_type_identifier =
| SomeTag of some_type * ... * some_type
| ...
| SomeTag of some_type * ... * some_type
```

+ `SomeTag` is a tag identifier, has to start with an uppercase letter
+ Tag identifiers must be unique and distinct
+ A tag characterizes one specific type in this disjoint union of types

Constructing tagged values

+ Tags are also called constructors
+ A tag is used as a marker to classify values with respect to the different cases of the union

```
SomeTag (some_expression, ..., some_expression)
```

+ Parentheses can be omitted if there is only one argument and if that argument is a simple expression

Case analysis by pattern matching

+ Pattern matching is done using a sequence of branches

```
match some_expression with
| some_pattern -> some_expression
| some_pattern -> some_expression
| ...
| some_pattern -> some_expression
```

+ There must be at least one branch in a pattern matching

Syntactic shortcut

```
let f x = match x with 
| some_pattern -> some_expression
| ...
| some_pattern -> some_expression
```

is the same as

```
let f = function
| some_pattern -> some_expression
| ...
| some_pattern -> some_expression
```


