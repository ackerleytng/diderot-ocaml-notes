# Functors

+ A functor is a module parameterized by another module.
+ It allows choice of implementation after compilation.

Syntax

```
module SomeModuleIdentifier (AnotherModuleIdentifier : SomeSignature) = struct
  ...
end
```

+ `SomeSignature` is the type of module that can be passed in. OCaml cannot infer module signatures

Syntax to apply a functor to a module, do

```
SomeModuleIdentifier (SomeModule)
```

where `SomeModule` is a module expression. A module expression could be a module identifier, an implementation, or a functor application (you can chain functor application).

The signature of a functor is

```
functor (ModuleIdentifier : SomeSignature) ->
  sig ... end
```

Example from the standard library

`Set` and `Map` both expect a module satisfying the following signature

```
module type OrderedType = signature
  type t
  val compare : t -> t -> int
end
```

So,

```
`Set.Make(E)` offers functions over sets of `E.t` elements
`Map.Make(E)` offers functions over maps with `E.t` keys
```

Type constraints

+ A type constraint expresses a fact about a type in a signature
+ A type constraint restricts the usage and definitions of functors
+ Syntax

```
some_signature with type some_type_identifier = some_type 
                and type some_type_identifier = some_type
                and ...
```
