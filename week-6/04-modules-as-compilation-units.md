# Modules as Compilation Units

Compiling OCaml programs

+ The file extension for OCaml source code is `.ml`
+ OCaml enjoys separate compilation:
    + Each file can be compiled separately following dependencies
    + All these compilation units can then be linked together
+ `ocamlc` compiles for the OCaml virtual machine
+ `ocamlopt` compiles to native code

Example:

+ Imagine that your project contains `a.ml` and `b.ml`, and `b.ml` depends on `a.ml`

1. Compile `a.ml`

```
ocamlc -c a.ml
```

This produces two files: 

+ `a.cmo` (bytecode) or `a.cmx` (native code, if we used `ocamlopt`)
+ `a.cmi` (compiled interface)

2. Compile `b.ml`

```
ocamlc -c b.ml
```

3. Link `a.cmo` and `b.cmo` into an executable, `prog`

```
ocamlc -o prog a.cmo b.cmo
```

The order of the `.cmo` files must follow the dependencies.

+ The interface of the module `a.ml` can be written in a file named `a.mli`.
+ When `a.ml` is compiled, the compiler looks for `a.mli` to compile the interface. If it does not exist, it uses the inferred module interface
+ Interfaces can also be compiled independently:

```
ocamlc -c a.mli
```

produces the file `a.cmi`

## `main` function?

+ There is no `main` function in an OCaml program.
+ The evaluation of a program is the evaluation of its modules
+ The modules are evaluated in the order given in the linking command

## Libraries

+ Several modules can be aggregated as a library into one `.cma` file

```
ocamlc -a a.cmo b.cmo -o lib.cma
```

+ This library can be used by another program as if it were a compilation unit
+ To install a library in a system, copy the compiled files (`.cmi`, `.cmo` and `.cma`) into an arbitrary directory `some_dir`
+ Compile another file `c.ml` with the library using

```
ocamlc -I some_dir -c c.ml
```

+ To use a library during linking

```
ocamlc -I some_dir -o prog lib.cma c.cmo
```

+ The `findlib` tool automates the library configuration and installation process

## Build system

+ OCaml comes with a build system tool called `ocamlbuild`
+ It automatically builds compiled files, libraries and executable programs
+ It automatically computes needed dependencies
+ It is configurable through a `_tag` file
+ It interacts with `findlib`
+ It is customizable using plugins
+ To build a program `a.byte` out of `a.ml` and its dependencies, just do

```
ocamlbuild a.byte
```

## Package manager

+ OCaml has a package manager named `opam`
+ A package may contain libraries and programs useful to other developments
