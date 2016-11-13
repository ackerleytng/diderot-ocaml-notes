# Mutable Data Structures: Arrays

+ OCaml's arrays are real arrays
+ Each cell of the array can be modified in place, using the `<-` operator
+ The old value is lost

The `update` operator `<-`

+ Allows in-place modification: `e1 <- e2`
+ The expression `e1` is evaluated
+ The type checker ensures that `e1` is a mutable value
+ The mutable value is modified in place with the new value `e2`
+ The type of the update operation is `unit`
