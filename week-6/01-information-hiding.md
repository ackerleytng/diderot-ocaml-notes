# Information Hiding

+ A module usually provides a well-delimited set of features
+ These features should come with a kind of user manual to indicate to users
    1. Function preconditions that have to be verified
    2. Data invariants that must be preserved
    3. Definitions on which the user must not rely, because they may change in future
+ A module signature represents a contract between the developer and user of a module. The type checker will enforce points 2 and 3

+ To constrain a module with a specific signature

```
module M : sig ... end = struct ... end
```

+ To name a signature

```
module type S = sig ... end
```
   
+ These names can also be used in module definitions

```
module M : S = struct ... end
```
