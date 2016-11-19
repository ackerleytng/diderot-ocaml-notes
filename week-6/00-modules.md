# Modules

An abstraction is a concept that can be understood intrinsically, without a precise knowledge of its implementation.

The module language of OCaml allows

+ a program to be divided into components
+ organization of identifiers to avoid naming conflicts
+ enforcement of layers of abstraction
+ easy combination of components

You can open the namespace of a module using `open`. For example, instead of `List.`, you can do `open List`, and then `length` will implicitly refer to `List.length`.

If two modules contain two identical identifiers, the definition from the last opened module is used

To define a module

```
module SomeModuleIdentifier =
struct
  (* a sequence of identifiers *)
end
```

The identifier of a module must start with an uppercase letter.

A module contains value, type and exception definitions.

A module can be aliased

```
module SomeModuleIdentifier = SomeOtherModuleIdentifier
```

The type of a module is called a signature or an interface.

OCaml can infer signatures, but publishing well-designed signatures is a very important communication aspect in a large project
:
```
sig
  (* A sequence of declarations of the form: *)
  val some_identifier: some_type
  type some_type_identifier = some_type_definition
  exception SomeException of some_type
end
```

Modules and signatures can be nested, but two submodules in a module cannot have the same name
