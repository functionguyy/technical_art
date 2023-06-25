# A COMPLETE INTRODUCTION TO VARIABLES IN C
A C program, whatever its size, consists of functions and variables. A function
contains statements that specify the computing operations to be done, and
variables store values used during the computation.

In this article, you will learn the meaning of a variable in C, how to declare
a variable and how to assign values to variables. You will learn about the different types of variables and the kind of
values they can store and, how to print the values stored in different types of
variables using `printf`. You will also learn about the `ASCII` character set and the different
scopes of variables in C. After reading this article you will have a good
understanding of variables in C and all it nuances.

## What is a variable in C?
In C, a variable is a symbolic name that represents a particular
storage location on the hard drive or any memory device connected to the
machine executing your program.

> “In C, all variables must be declared before they are used, usually at the
> beginning of the function before any executable statements.” – K & R

To declare a variable in C programming, we first specify the type of the
variable, then its identifier.

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
identifier in C:

- It must start with an alphabet(the underscore `_` counts as an alphabet).
- It must not have any spaces inbetween.
- It must be unique and must not be a keyword in C.
- It can be made up of uppercase or lowercase alphabetic characters, the 10.
digits and the underscore `_`.

```C
/* example of valid indentifiers */
sum
Flag
i
Sum
mem_alloc
x5j6
SUM

/* example of invalid identifiers */

sum$value /* $ is not a valid character */
piece flag /* Embedded spaces are not permitted */
3spencer /* Variable names cannot start with a number */
int /* int is a  keyword in C */
```
**Uppercase and lowercase letters are distinct in C. Therefore, the identifiers
`sum`, `Sum`, and `SUM` are different.**

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
To declare a variable in C programming, we first specify the type of the
variable, then its identifier. For example we might declare variables
"height" and "profit" as:

```C
int height;
float profit;
```
The first declaration states that `height` is a variable of type `int`, which
means that `height` can store whole numbers. The second declaration states that
`profit` is a variable of type `float`, which means that `profit` can store
numbers with digits after the decimal points.

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

Compile the program below on your Bash/terminal and run its output file to
print out the memory allocation specification for each of the fundamental C types on
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
[image of output]

**The type specified for a variable determines the range of values that the
variable can store.**

C takes portability(ability of your program to compile on different kinds of
machines) seriously and actually bothers to tell you what values and ranges are
guaranteed to be safe for each **type**. Continue reading to learn more about
the different types and their range of values.

### Integer Type
An integer type variable will store integer constants. In C, we use the keyword
`int` to specify that a declaration is an integer type.

An integer constant consist of a sequence of one or more digits. A minus sign
before the sequence indicates that the value is negative. No embedded spaces are
permitted between the digits, and values larger than 999 cannot be expressed
using commas. C allows integer constants to be written in decimal(base 10),
octal (base 8), or hexadecimal (base 16).

Decimal integer constant contain digits between 0 and 9. They must not begin
with a zero:
```C
/* examples of valid integer constant */
-10
255
11000
```
Octal integer constants contain only digits between 0 and 7. They must begin
with a zero:
```C
/* example of valid octal integer constants */
017
0377
0777777
```
Hexidecimal integer constants contain digits between 0 and 9 and letter between
a and f. They must begin with 0x:
```C
/* examples of valid hexadecimal integer constant */
0xff
0xfF
0x1A
0xAB
```
An integer type variable can be declared as one of two forms; **signed** or
**unsigned**. By default, a variable declared with the keyword `int` is a **signed**
integer type variable. This means it can store either negative or positive
integer constants. To declare an **unsigned** integer type variable, we use the
keyword `unsigned int`. An **unsigned** integer type variable can only store
positive integer constants.

To print the value stored in a variable with the `printf` function we use a
format specifier.

`%d` is the format specifier used to print the value stored in a **signed**
integer type variable while `%u` is the format specifier used to print the value
stored in an **unsigned** integer type variable.

```C
/* code example of printing base signed and unsigned integer type variables */
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
[image of output]

For both `signed` and `unsigned` integer types, C provides 3 subtype
flavors to allow us construct an integer type variable that meets our needs.
The reserved keyword to specify each subtype flavors are:

- `unsigned short int`
- `unsigned int`
- `unsigned long int`
- `signed short int`
- `signed int`
- `signed long int`

 C allows us to abbreviate the subtype keywords in our codes by dropping the word
 `int` and `signed`. For example, `unsigned short int` can be abbreviated to `unsigned
 short` and `signed long int` can be abbreviated to just `long`. Omitting `int` and
 `signed` this way is a widespread practice among C programmers.

`%lu` is the format specifier used to print the values of `unsigned long int`
variables while `%ld` is used to print the values of `signed long int`
variables. To print the values stored in `unsigned short int` and
`signed short int` variables use the format specifier `%u` and `%d` respectively.

> The return value of most C standard library functions are unsigned long integers.
> Check the earlier code snippet example that used the `sizeof` function to see how to
> print an unsigned integer.

The integer type subtype you specify in a variable's declaration determines the
range of values that can be stored through the variable. This range of values
represented by each of the subtypes varies from one machine to another.

The following table shows the memory that will be allocated and the range of
values that can be assigned to a variable declared with any of the integer type
subtypes on most 64-bit Linux machines:

|Type | Memory allocation | Value range
--- | --- | ---
`short` | 2 bytes | -32,768 to 32,767
`unsigned short` | 2 bytes | 0 to 65,535
`int` | 4 bytes | -2,147,483,648 to 2,147,483,647
`unsigned int` | 4 bytes | 0 to 4,294,967,295
`long` | 8 bytes | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
`unsigned long` | 8 bytes | 0 to 18,446,744,073,709,551,615

C allows us to abbreviate the keywords of integer types subtypes in our codes by
dropping the word `int` and `signed`. For example, `unsigned short int` may be
abbreviated to `unsigned short`, and `signed long int` can be abbreviated to just
`long`. Omitting `int` this way is a widespread practice among C programmers.

#### Signed vs Unsigned (optional read)

In C programming, unsigned integers are  preferred over signed integers because
[unsigned integers are more efficient](https://embeddedgurus.com/stack-overflow/2009/05/signed-versus-unsigned-integers/).
Also unsigned integers produce defined results for
[modulo arithmetic overflow](https://embeddedgurus.com/stack-overflow/2009/08/a-tutorial-on-signed-and-unsigned-integers/#:~:text=To%20convert%20a%20signed%20integer%20to%20an%20unsigned,c%3B%20b%20%3D%20%28unsigned%20int%29a%3B%20c%20%3D%20%28int%29b%3B)


### Character types

A character type variable will store character constants and manipulate string
literals. In C, we use the keyword `char` to specify that a declaration is a
character type.

In this section, I will focus only on how `char` type variables store character
constants because the discussion of how `char` type variables manipulate string
literals is beyond the scope of this article.

Character constants are characters that are represented in a character set. In
C, a character in a single quote `''` forms a character constant.

```
'v'
```

A character set is a system used to reperesent characters
with codes that are understood by computers. A popular type of character set is
the **American Standard Code for Information Interchange(ASCII)** character set.

The following are represented with whole numbers in **ASCII**:
- Uppercase and lowercase letters of the alphabet.
- digits 0 to 9.
- Special characters in C.

**ASCII** is capable of representing 128 different characters.

The character constants a `char` type variable can store varies from one
computer to another, because different machines may have different underlying
character sets. The **ASCII** character set is available on most Linux machines.

```C
char aCharConst;

/* sample of character constants that can be stored in a char type variable */

aCharConst = 'b'; /* lower-case b */
aCharConst = '\n'; /* new line special character */
aCharConst = '0'; /* digit 0 */
aCharConst = ' '; /* space */
aCharConst = 'B'; /* upper-case B 8/
```

**It is important to note that character constants are enclosed in single quotes,
not double quotes: `'b'` is not the same as `"b"`.**

`%c` is the format specifier used to print character constants.
```C
#include <stdio.h>

int main(void)
{
	/* variable declaration */
	char ch; /* char type variable */

	/* variable assignment */
	ch = 'W';

	/* print the value stored in the variables */
	printf("The character constant stored in variable ch is %c\n", ch);

	return (0);
}

```
[image of output]


C treats character constants as small integers, which means character constants
can be used in arithmetic computation. When a character constant appears in an
arithmetic computation, C simply uses the integer value that represents the
character constant in the underlying character set on the machine executing the program.

```C
#include <stdio.h>

int main(void)
{
	/* variable declarations */
	char ch; /* char type variable */
	int i; /* int type variable */

	/* variable assignments */
	i = 65;
	ch = i + 'a'; /* C will translate the character constant to its integer value in ASCII */

	/* print values stored in the different types of variables */
	printf("The value stored in variable "i" is: %d\n", i);
	printf("The character constant stored in variable "ch" is: %c\n", ch);

	return (0);
}

```
[image of output]

The difference between a `char` type variable and any `int` type variable
is their respective storage allocation and range of values. `char` type
variables use a lesser storage allocation and accepts a smaller range of values.

Also since C allows character constants to be used as integers in
computation, a `char` type variable can exits in both `signed` and `unsigned`
flavors.

The following table shows the storage allocation specification and range of
values for the different flavours of `char` type variables:

Type | Memory allocation spec | Value range
--- | --- | ---
`signed char` | 1 byte | -128 to 127
`unsigned char` | 1 byte | 0 to 255

The C standard doesn't define whether just specifing `char`  in a variable
declaration indicates a signed type or an unsigned type. some compilers treat
ordinary `char` as a signed type, while others treat it as an unsigned type.
(Some even allow the programmer to select, via a compiler option whether `char`
should be signed or unsigned). Most of the time it doesn't really matter
whether `char` is signed or unsigned.

> Don't assume that `char` is either signed or unsigned by default. if it
> matters, use `signed char` or `unsigned char` instead of `char`.

### Floating types
A floating type variable will store floating-point constants. In C, we use the
keyword `float` to specify that a declaration is a floating type.

floating-point constants are values that contain digits after the decimal
point. You omit digits before the decimal point or digits after the decimal
point, but you can't omit both. Floating-point constants can also be expressed
in *scientific notation*.
```C
/* example of valid floating-point constants */
3.
120.8
-.0001
1.7e4 /* scientific notation for 1.7 * 10^-4 */
2.5E+1 /* scientific notation for 2.5 * 10^1 */
```
C provides three (3) floating types keywords, corresponding to to different
floating-point formats:
- `float` Single-precision floating-point
- `double` Double-precision floating-point
- `long double` Extended-precision floating point

The C standard doesn't state how much precision the `float`, `double`, and
`long double` types provide, since different computer may store floating-point
numbers in different ways. Most modern computers follow the specifications in
IEEE standard 754 (also known as IEC 60559).

By default, all floating-point constants are stored as double-precision values
by the C compiler. This means for example when a C compiler finds a constant
120.8 in your program, it arranges for the number to be stored in memory in the
same format as a `double` variable.

`%f`, `%e` or`%g` is the format specifier used to print floating-point constants with
`printf`. The format specifier `%g` produces the most aesthetically pleasing
output because it lets `printf`decide whether to display the floating-point
constant in normal floating-point notation or in scientific notation.
```C
#include <stdio.h>

int main(void)
{
	float profit;
	double temp;

	profit = 12.50;
	temp = -4.6;


	printf();
	printf();

	return (0)
}
```


## Scope of variables
A declared variable may only be use in a function, within a single source file
or, multiple source files of the entire program.
