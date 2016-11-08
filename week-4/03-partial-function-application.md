# Partial Function Application

+ These two functions are alike

```
let f1 = fun x y -> exp
let f2 = function x -> function y -> exp
```

Examples

```
let f1 = fun x y z -> x + y * z

let f2 = f1 1

let f3 = f2 2

f3 4
(* gives 9 *)
```

Function application:

+ Applying `function x -> exp` to `a` means evaluating `exp` in the context of `x = a`
+ The body of a function is not evaluated when the function is defined, but only when it is applied
