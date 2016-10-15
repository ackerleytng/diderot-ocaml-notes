# Definitions

Global Definitions

+ Give names to values
+ `global` = effective for the rest of the `toplevel` session
+ Syntax: `let name = expression`
+ Immutable

Local Definitions

+ Naming values with limited scope
+ Syntax: `let name = exp1 in exp2`
+ Scope of `name` is `exp2`
+ A local definition may temporarily hide a more global one
+ Sequential definitions

```
let name =
  let name2 = exp2 in
  exp3;;
```

+ Simultaneous definitions

```
let name = exp1
  and name2 = exp2 in 
    exp3;;
```
