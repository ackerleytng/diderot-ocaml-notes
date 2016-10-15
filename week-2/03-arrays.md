# Constructing and Observing Arrays

+ Tuples and records have statically bounded sizes
+ Arrays allow us to define composite values whose size is dynamically defined
+ All array elements must have the same type

```
let p = [| 1; 2; 3 |];;
```

Generating arrays

```
# let square x = x * x;;
# let squares n = Array.init n square;;
# let s1 = squares 5;;
val s1 : int array = [|0; 1; 4; 9; 16|]
```

+ The type of an array whose elements have `some_type` is 

```
some_type array
```

+ `array` is a predefined type constructor

+ Arrays whose elements and sizes are known at compile time are written as

```
[| some_expression; ...; some_expression |]
```

+ `Array.make` expects an integer representing the size of the array and a ***value*** to initialize each component of the array
+ `Array.init` expects an integer representing the size of the array and a ***function*** to initialize each component of the array
    + The initialization function is given the index of the component and must return its value
+ `Array.length` returns the size of an array

+ To observe a component of an array using an index:

```
some_expression.(some_expression)
```

+ Indices have values between 0 and `Array.length array - 1`
+ To observe several components of an array, one can use array patterns

```
[| some_pattern; ...; some_pattern |]
```

Implementation in the machine

+ An array is a heap-allocated block
