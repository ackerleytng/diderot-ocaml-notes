# Constructing and Observing Records

+ Record types must be declared

```
type some_type_identifier = 
  { field_name : some_type; ...; field_name: some_type }
```

+ All field names must be distinct

+ Constructing a record

```
{ field_name : some_expression; ...; field_name: some_expression }
```

+ All fields must be defined in a constructor

+ To observe a specific field

```
some_expression.field_name
```

+ Observe multiple fields using record patterns

```
{ field_name : some_pattern; ...; field_name: some_pattern }
```

+ The record pattern may not mention all fields

Implementation in the machine

+ A record is represented by a heap-allocated block
+ A record is represented exactly as a tuple

Field name collisions

+ With this,

```
type a = { x : int; b : int; };; 
type b = { y : int; c : int; };; 
```

+ This will be identified correctly to be of type `a`

```
{ x = 0; b = 2 };;
```

With this, 

````
type t = { x : bool };;
type u = { x : int };;
```

+ This will fail type checking, since `u`, the last thing entered in `toplevel`, expects an `int` for `x`

```
{ x : true }
```
