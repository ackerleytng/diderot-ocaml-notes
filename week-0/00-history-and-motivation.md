# History and Motivation

+ Computing: the study of algorithmic processes that describe and transform automation
+ A program describes the intended transformation of information
+ Imperative program: read, write and perform operations, take decisions based on contents of memory cells
+ Alonzo Church (Turing's advisor) proposed lambda calculus, which is about 
    + Abstractions (or functions)
    + Applications (or function called on arguments)
+ Beta reduction rule: replacing parameter with argument, apply function

+ In a functional program, we define functions (possibly recursive) and compose and apply them to compute expected results
+ Functions are first class citizens, they can be
    + Named
    + Evaluated
    + Passed as arguments
    + Returned as results
+ Basically, they can be used everywhere an expression can fit

+ A function is computable by a Turing machine iff it is computable using lambda calculus
+ A function that is computable by any computing device is also computable by a Turing machine
+ All general purpose computing languages are computationally equivalent

+ Programming languages have different levels of expressiveness
    + Different data representations
    + Different execution models
    + Different mechanisms of abstraction
+ Differing features
    + Safety of execution
    + Efficiency
    + Maintainability
    
+ Why functional programming is on the rise
    + Need for greater software reliability
        + Pure functional programs are easier to prove correct than imperative ones
    + A carefully chosen set of higher order functions allows us to write programs that are easily parallelisable

