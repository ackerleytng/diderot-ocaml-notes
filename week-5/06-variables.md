# Variables aka References

OCaml has a predefined `ref` type.

```
type 'a ref = { mutable contents: 'a }
```

Syntax:

+ `ref` creates the reference
+ `!` reads the reference
+ `:=` as in `r := v` updates the content of the reference `r` with `v`

Example

```
let log2int n =
  let count = ref 0 and v = ref n in
  while !v > 1 do
    count := !count + 1;
    v := !v / 2
  done;
  !count
```

Example: reading a list of integers

```
let read_intlist () =
  let l = ref [] in
  let doread () =
    try
      while true do
        l := (read_int ()) :: !l
      done
    with _ -> ()
  in
  doread () ; List.rev !l
```
