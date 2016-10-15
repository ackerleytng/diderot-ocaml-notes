# User-defined Types

Types as documentation

+ A value of a primitive type can be used to encode some data
+ A type identifier carries an informal invariant

Example: colors

```
type color = int;;
let red : color = 0;;
let white : color = 1;;
let blue : color = 2;;
```

Example: `abs`

```
type positive = int;;
let abs (x : int) = (if x < 0 then -x else x : positive);;
let abs' (x : int) : positive = if x < 0 then -x else x;;
```

Syntax

+ Declaration

```
type some_type_identifier = some_type;;
```

+ `some_type_identifier` is a synonym or abbreviation for `some_type`
+ A type identifier must start with a lowercase letter

+ Annotate an identifier with a type

```
let x : some_type = some_expression
```

+ Annotate a function argument with a type

```
let f (x : some_type) = some_expression
```

+ Constrain a return type of a function

```
let f x : some_type = some_expression
```

+ Constrain a type of an expression

```
let f x = (some_expression : some_type)
```

+ Type annotations have no impact on program execution

+ Type synonyms only act as documentation
+ Type synonyms don't provide static guarantees
