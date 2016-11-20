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

Example of a well-designed signature

```
module Naturals :
sig
  type t
  val zero : t
  val succ : t -> t
  val pred : t -> t
end
  
open Naturals
let rec add : t -> t -> t = fun x y -> 
  if x = zero then y else succ (add (pred x) y)
```

This signature is good because

+ The definition of type `t` has been hidden, so users of this module cannot abuse the knowledge that `t` is an `int` and potentially break the abstraction.
+ The typechecker will enforce this
+ `t` is called an abstract type

Private definitions

+ The programmer can choose not to export some definitions
+ This is convenient to hide private internal functions

```
module Naturals :
sig
  type t
  val zero : t
  (* Since return_natural is not exposed, it can't be used by other functions *)
  val succ : t -> t
  val pred : t -> t
end = struct
  type t = int
  let zero = 0
  let return_natural n = assert (n >= 0 && n <= max_int); n
  let succ n = if n = max_int then 0 else return_natural (n + 1)
  let pred = function 0 -> 0 | n -> n - 1
end
```
