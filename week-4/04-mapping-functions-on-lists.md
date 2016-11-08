# Mapping Functions on Lists

The library module `List`

+ "import" using `open List` or call using pointed notation, like `List.hd`

```
map (function x -> x*x) [1;2;3;4;5]
(* gives [1; 4; 9; 16; 25] *)

map2 (fun x y -> x+y) [1;2;3] [10;20;30]
(* gives [11; 22; 33] *)
```

+ To turn an infix operator into a function, use parentheses: `(+)`, `(/)`, etc.
    + Special case for multiplication: `( * )`

Examples

```
let vsum = List.map2 (+)

vsum [1;2;3] [10;20;30]
(* gives [11; 22; 33] *)
```

I like this example of how sublists are generated. It's so elegant!!

Idea:

+ The sublists of `[]` is `[[]]`
+ if `l = h :: r`, then any sublist of `l`
    + either is some sublist of `r`
    + or is obtained from some sublist of `r` by putting `h` in front

```
let rec sublists = function 
  | [] -> [ [] ]
  | h :: r ->
     let rp = sublists r in
     rp @ (List.map (function l -> h :: l) rp)

sublists [1;2;3]
(* gives [[]; [3]; [2]; [2; 3]; [1]; [1; 3]; [1; 2]; [1; 2; 3]] *)
```
