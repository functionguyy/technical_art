# A COMPLETE INTRODUCTION TO VARIABLES IN C
A C program, whatever its size, consists of functions and variables. A function
contains statements that specify the computing operations to be done, and
variables store values used during the computation.


In this article, you will learn about the different types of variables in C,
you will learn how to declare the appropriate variables for a computation in a
C program and also learn how use variables

## What is a variable in C?
A variable in C is an identifier for a reserved storage location on the hard
drive or any memory device attached to the machine running your program.

> “In C, all variables must be declared before they are used, usually at the
> beginning of the function before any executable statements.” – K & R

A declared variable may only be use in a function, within a single source file
or, multiple source files of the entire program.

To declare a variable in C, means to define a type with an identifier.

```C
/* structure of variable declaration in C */

type identifier; /* single variable declaration */

type identifier_1, identifier_2, identifier_3; /* multiple variable declaration with same type */
```

## What is an identifier?
Identifier is the fancy term used to mean ‘name’. In C, identifiers are used to
refer to names of variables, functions, macros, and other entities.

The rules for the construction of identifiers are simple:
- An identifier must start with an alphabet.
- It must be unique and must not be a keyword in C
- It can be made up of uppercase or lowercase alphabetic characters, the 10
digits and the underscore `_`.

## What is a type?
A type is the classification that specify the kind of values a variable can
store.

C is a statically typed language. This means that before a variable can be used
it must first be declared with a specific type. The type of a variable
specifies to the compiler

- The kind of values that are acceptable to be stored through the variable
- The acceptable range of values that can be stored through the variable
- The amount of storage space that should be reserved for the variable
- The computations that should be allowed to be performed with the variable

If any of the above conditions cannot be satisfied for the specified type of a
variable, the compiler generates an error message.

## How to declare a variable in C?
To declare a variable, we first specify the type of the variable, then its
identifier. For example, we might declare variables “height” and “profit” as
follows:
```C
int height;
float profit;
```
The first declaration states that height is a variable of type int, meaning
that height can store whole numbers. The second declaration says that profit is
a variable of type float, meaning that profit can store numbers with digits
after the decimal points.

After a variable has been declared it can be initialized (given a value) by
means of assignment:
```C
height = 8;
profit = 21.50;
```
## Basic types in C

C supports three (3) basic types for declaring variables:
- Integer types
- Floating types
- Character types

To specify any of the basic types in a variable declaration, we use the dedicated
keywords provided for each of them in the C standard:

- `int` is the keyword used to specify an integer type variable
- `float` is the keyword used to speicify a floating type variable
- `char` is the keyword used to specify a character type variable

## What happens in your computer when you declare a variable in C?
When you declare a variable in C, you are basically introducing the variable to
the program. As a result of the declaration the compiler now knows that it
needs to reserve storage space for the variable on the hard drive of the
computer running the program.

As the compiler compiles your program, it writes machine code that instructs
your computer to reserve a specific amount of memory on the hard drive for each
variable declared inside your program and then labels the reserved memory
locations with the respective identifiers of each variable. It is this reserved
memory that then acts as a storage for the values that you assign to the
variables.

The specific amount of memory that is reserved for each type of variable is
determined by CPU architecture of your computer. Different CPU architectures
have different defined memory sizes for each C basic types.


The storage size of the basic C types on most 64-bit Linux machines are as
follows:

Type | Storage size
--- | ---
`char` | 1 byte
`int` | 4 bytes
`float` | 4 bytes

To know the storage size defined for each of the above types on your computer,
use the `sizeof` operator.

```C
/* filename: sizes.c */

#include
```

**The how the type specified for a variable affects the range of values that
the variable can store so let’s spend some time to talk about the basic types in C.**

Let’s talk briefly about each of the types.

## Integer Type
An integer type variable will store whole numbers. The keyword used to specify
an integer type is `int`.

The integer types are divided into two categories:
- **Signed** integer types
- **Unsigned** integer types

By default, variables declared with keyword `int` can store **signed** integer types.
This means these variables can store both negative and positive whole numbers.

To declare a variable that can store only positive whole numbers we use the
`unisigned int` keyword.

C provides six keyword flavors for integer types to allow us construct an
integer type variable that meets our needs. The reserved keyword to specify
each integer type flavor are:
- `short int`
- `unsigned short int`
- `int`
- `unsigned int`
- `long int`
- `unsigned long int`

The integer type flavor you choose to define for a variable will determine the
range of values you can store through the variable.

The range of values represented by each of the six integer types varies from
one machine to another. However, the table below shows the range of values for
each integer type flavors on most 64-bits Linux machines.
|Type | st
