# Sequences and Iterations

We can use functions with side effects to 

+ Create sequences
+ Write loops

Expression sequences

The expression sequence

```
e1 ; e2 ; ... ; en
```

means evaluate each `ei` in turn, then drop all the results but the last one.

+ It returns the result of `en`
+ All intermediate expressions should be of type `unit`, otherwise the OCaml compiler prints a warning
+ Watch out, binding begins from the left, so the following parentheses apply by default

```
(if 3 > 5 then print_string "3 is greater than 5") ; print_string "."
```

You have to either wrap it in parentheses or use `begin` and `end`.

```
if 3 > 5 then
  begin print_string "3 is greater than 5";
        print_string "."
  end
```

Iterations

Example: printing integers from 1 to 10 (functionally)

```
let foreach starti endi f =
  let rec aux =
    function n -> if n <= endi
                  then (f n; aux (n + 1))
                  else ()
  in aux starti
```

The `for` loops

```
for i = 1 to 10 do
  print_int i
done
```

or more generally,

```
for id = e1 to e2 do e3 done
```

+ the loop identifier if takes all integer values from `e1` to `e2` in turn, and cannot be otherwise altered
+ the loop body `e3` is evaluated for each value of `id`
+ the type of the for loop is `unit` 
+ the type of the loop body is expected to be `unit`, otherwise the OCaml compiler prints a warning

Going downwards:

```
for i = 10 downto 1 do
  print_int i
done
```

The `while` loop

```
while e1 do e2 done
```

+ the condition `e1` is evaluated
+ if `true`, the loop body `e2` is evaluated, and the loop repeats.
+ if `false`, the loop stops
+ the type of the while loop is unit, and the type of the loop body is also expected to be unit

The `ignore` function can be used to suppress the warnings resulting from using values in the body of a loop that is not of the `unit` type. The `ignore` function converts anything to a `unit` type.
