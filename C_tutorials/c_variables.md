# A COMPLETE INTRODUCTION TO VARIABLES IN C
A C program, whatever its size, consists of functions and variables. A function
contains statements that specify the computing operations to be done, and
variables store values used during the computation.

In this article, you will learn about the different types of variables in C,
you will learn how to declare the appropriate variables for a computation in a
C program and also learn how use variables

## What is a variable in C?
In C, a variable is a symbolic name that represents a particular
storage location on the hard drive or any memory device connected to the
machine executing your program.

> “In C, all variables must be declared before they are used, usually at the
> beginning of the function before any executable statements.” – K & R

You specify a type with an identifier to declare a variable.

```C
/* structure of variable declaration in C */

type identifier; /* single variable declaration */

type identifier_1, identifier_2, identifier_3; /* multiple variable declaration with the same type */
```
## What is an identifier?
An identifier is any name you provide for variables, functions, macros, and
other data structures in your program. You're required to construct a valid
identifier.

The following list indicates the rules you must follow to construct a valid
identifier:

- it must start with an alphabet(the underscore `_` counts as an alphabet).
- it must not have any spaces inbetween.
- It must be unique and must not be a keyword in C.
- It can be made up of uppercase or lowercase alphabetic characters, the 10.
digits and the underscore `_`.

```C
/* example of valid indentifiers */
sum
Flag
i
mem_alloc
x5j6

/* example of invalid identifiers */

sum$value /* $ is not a valid character */
piece flag /* Embedded spaces are not permitted */
3spencer /* Variable names cannot start with a number */
int /* int is a  keyword in C */
```
**You should always remember that uppercase and lowercase letters are distinct
in C. Therefore, the identifiers `sum`, `Sum`, and `SUM` are different.**

Programming best practices recommends that you construct identifiers that
reflects their intended use.

## What is a type?
A type is the classification that specify the kind of values an identifier can
store or manipulate.

C is a statically typed language. This means all identifiers must be associated
with a type.

The type specified for an identifier indicates the following to the compiler:

- The kind of values that are acceptable to be stored through the identifier
- The acceptable range of values that can be stored through the identifier
- The amount of storage space that should be reserved for the identifier
- The computations that should be allowed to be performed with the identifier

If any of the above conditions cannot be satisfied for the specified type of an
identifier, the compiler generates an error message.

## Fundamental types in C
C supports three (3) fundamental types:

- Integer types
- Floating types
- Character types

To specify any of the fundamental types in a variable declaration, we use the dedicated
keywords provided for each of them in the C standard:

- `int` is the keyword used to specify an integer type variable
- `float` is the keyword used to speicify a floating type variable
- `char` is the keyword used to specify a character type variable

## How to declare a variable in C?
To declare a variable, we first specify the type of the variable, then its
identifier. For example, we might declare variables “height” and “profit” as
follows:
```C
int height;
float profit;
```
The first declaration states that `height` is a variable of type `int`, meaning
that height can store whole numbers. The second declaration says that `profit` is
a variable of type `float`, meaning that profit can store numbers with digits
after the decimal points.

After a variable has been declared it can be initialized (given a value) by
means of assignment:
```C
height = 8;
profit = 21.50;
```
## What happens in your computer when you declare a variable in C?
When you declare a variable in the C programming language, you essentially
introduce the variable to the program. This declaration informs the compiler
that it should allocate storage space for the variable on the computer's hard
drive while running the program.

While compiling your program, the compiler generates machine code that directs
your computer to allocate a designated portion of memory on the hard drive for
every declared variable in your program. It subsequently assigns corresponding
identifiers to the allocated memory locations. This allocated memory serves as
storage for the values assigned to the variables.

The CPU architecture of your computer determines the precise amount of memory
allocated for each variable type. Various CPU architectures have distinct
memory allocation specifications for the fundamental C types.

Memory allocation is generally defined in **bytes** but computer's translate
memory allocation in **bits**
```
1 byte = 8 bits
```

On most 64-bit Linux machines, the memory allocation specifications for the
fundamental C types are as follows:

Type | memory allocation
--- | ---
`char` | 1 byte
`int` | 4 bytes
`float` | 4 bytes


To obtain the memory allocation specifications for each of the fundamental C
types on your computer, you can use the standard library function `sizeof`.

If you compile and run the program below on your Bash/terminal it will print
out the memory allocation specification for each of the fundamental C types on
your computer:

```C
/* filename: type_sizes.c */

#include <stdio.h>

int main(void)
{
	printf("Size of type 'char' on my computer: %lu bytes\n", sizeof(char));
	printf("Size of type 'int' on my computer: %lu bytes\n", sizeof(int));
	printf("Size of type 'float' on my computer: %lu bytes\n", sizeof(float));

	return (0);
}

```

**The type specified for a variable affects the range of values that the
variable can store.**

C takes portability seriously and actually bothers to tell you what values and
ranges are guaranteed to be safe for each **type**. So, let’s talk briefly
about each of the types.

## Integer Type
An integer type variable will store whole numbers. The keyword used to specify
an integer type is `int`.

A whole number is

An integer type variable can be declared as one of two forms:
- **Signed** integer types
- **Unsigned** integer types

Variables declared with keyword `int` are **signed** integer types. This means
they can store both negative and positive whole numbers.

Variables declared with keyword `unsigned int` are **unsigned** integer types.
this means they can only store positive whole numbers.


To print the value stored in a variable with the `printf` function we use a
format specifier.

The format specifier for printing the value stored in a **signed** integer type
variable is `%d` while `%u` is the format specifier for printing value stored in an
**unsigned** integer type variable.
```C
/* code example of printing signed integers */
#include <stdio.h>

int main(void)
{
	/* variable declarations */
	int score_point;
	int height;
	unsigned int age;

	/* variable assignment or initialization */
	score_point = -10;
	height = 8;
	age = 40;

	/* printing values assigned to the variable */
	printf("This is the final score point: %d\n", score_point);
	printf("This is the height of the player: %d\n", height);
	printf("The player is %u years old", age);

	return (0);
}

```

For both `signed` and `unsigned` integer types, C provides 3 flavors to allow
us construct an integer type variable that meets our needs. The reserved keyword to specify
each subtypes are:

- `unsigned short int`
- `unsigned int`
- `unsigned long int`
- `signed short int`
- `signed int`
- `signed long int`


`%lu` is the format specifier used to print the values of `unsigned long int`
variables while `%ld` is used to print the values of `signed long int`
variables. For the `unsigned short int` and `signed short int` variables use the
format specifier `%u` and `%d` respectively.

The integer type flavor you specify in a variable's declaration determines the
range of values that can be stored through the variable. This range of values
represented by each of the integer type flavors varies from
one machine to another.

The following table shows the range of values for each flavor of an integer
type variable on most 64-bits Linux machines:

|Type | Memory allocation | Value range
--- | --- | ---
`short` | 2 bytes | -32,768 to 32,767
`unsigned short` | 2 bytes | 0 to 65,535
`int` | 4 bytes | -2,147,483,648 to 2,147,483,647
`unsigned int` | 4 bytes | 0 to 4,294,967,295
`long` | 8 bytes | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
`unsigned long` | 8 bytes | 0 to 18,446,744,073,709,551,615

C allows us to abbreviate the keywords of integer types flavors by dropping the
word `int`. For example, `unsigned short int` may be abbreviated to `unsigned
short`, and `long int` may be abbreviated to just `long`. Omitting `int` this
way is a widespread practice among C programmers.



## Character types
A character type variable will store characters. The keyword used to specify a
character type is `char`.

`char` is just another sort of integer type, but has a different application;
It is used to store character constants. Character constants are whole numbers
which are represented in a character set. A character in a single quote `''`
forms a character constant.

```C
'b'

```
The values a `char` type can store varies from one computer to another, because different
machines may have different underlying character sets.

C supports the **ASCII** character set. This character set is available on most
linux machines.

It is important to note that character constants are enclosed in single quotes,
not double quotes: `'b'` is not the same as `"b"`.


The difference between a `char` type variable and any `int` type variable
is their respective storage allocation and range of values. A `char` type
variable uses a lesser storage allocation and accepts a smaller range of values.

The following table shows the storage allocation specification and range of
values for a `char` type variable:

## Scope of variables
A declared variable may only be use in a function, within a single source file
or, multiple source files of the entire program.
