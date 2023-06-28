# A COMPLETE INTRODUCTION TO VARIABLES IN C
All C programs, whatever their size, consists of functions and variables. A
function contains statements that specify the computing operations to be done,
and variables store values used during the computation.

In this article, you will learn the meaning of a variable in C, how to declare
a variable and how to assign values to variables. You will learn about the
different types of variables and the kind of values they can store and, how to
print the values stored in different types of variables using `printf`. You
will also learn about the `ASCII` character set and the different
scopes of variables in C. After reading this article you will have a good
understanding of variables in C and all it nuances.


## What is a variable in C?
In C, a variable is a symbolic name that represents a particular
storage location on the hard drive or any memory device connected to the
machine executing your program.

> “In C, all variables must be declared before they are used, usually at the
> beginning of the function before any executable statements.” – K & R

To declare a variable in C programming, we first specify the Type of the
variable, then its identifier.

```C
/* structure of variable declaration in C */

Type identifier; /* declaration of a single variable */

Type identifier_1, identifier_2, identifier_N; /* declaration of multiple variables with the Type */
```
## What is an Identifier?
An Identifier is any name you provide for variables, functions, macros, and
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

Programming best practices recommends that you construct Identifiers that
reflects their intended use.

## What is a Type?
A Type is the specification that describes the kind of
values an identifier can store or manipulate.

C is a statically typed language. This means all identifiers must be associated
with a Type.

The Type specified for an identifier indicates the following to the compiler:

- The kind of values that are acceptable to be stored through the identifier
- The acceptable range of values that can be stored through the identifier
- The amount of storage space that should be allocated for the identifier
- The computations that should be allowed to be performed with the identifier

If any of the above conditions cannot be satisfied for the specified type of an
identifier, the compiler generates an error message.

### Fundamental Types in C
C supports three (3) fundamental Types:

- Integer types
- Floating types
- Character types

To specify any of the fundamental Types in a variable declaration, we use
the dedicated keywords provided for each of them in the C standard:

- `int` is the keyword used to specify an Integer type
- `float` is the keyword used to speicify a Floating type
- `char` is the keyword used to specify a Character type

You might have heard or seen people use the term Datatype and you're wondering
what the difference is between Datatype and Type. Although both terms can be
used interchangeably, they have slightly different meanings; Type refers to a
specification while Datatype refers to data that fits a Type specification.

So when we specify a *Type* in a Variable declaration, we're instructing the
compiler to make a Variable that can store *Datatypes* that fits the
specifications of the *Type* specified for the Variable.

## How to declare a variable in C?
To declare a variable in C programming, we first specify the Type of the
variable, then its Identifier. For example we might declare variables
"height" and "profit" as:

```C
int height;
float profit;
```
The first declaration states that `height` is a variable of Type `int`, which
means that `height` can store whole numbers. The second declaration states that
`profit` is a variable of Type `float`, which means that `profit` can store
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
to allocate storage space for the variable on the computer's hard
drive while running the program.

While compiling your program, the compiler generates machine code that directs
your computer to allocate a designated portion of memory on the hard drive for
every declared variable in your program. It subsequently assigns corresponding
identifiers to the allocated memory locations. This allocated memory serves as
storage for the values assigned to the variables.

The CPU architecture of your computer determines the precise amount of memory
allocated for each variable type. Different CPU architectures have distinct
memory allocation specifications for the fundamental C types.

Memory allocation is generally defined in **Bytes** but computer's translate
memory allocation in **Bits**
```bash
1 Byte = 8 Bits
```
The following table shows the memory space that will be allocated for Variables
declared with the fundamental C Types on most 64-bit Linux machines:

Type | memory allocation
--- | ---
`char` | 1 Byte
`int` | 4 Bytes
`float` | 4 Bytes


To obtain the memory allocation specifications for each of the fundamental C
Types on your computer, you can pass the Type keyword as an argument to the
standard library function `sizeof`and print its return value with the `printf`
function.

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

We use a format specifier to print the value stored in a Variable with the
`printf` function. In the above code snippet, the format specifier `%lu` is
used in the `printf` function to print the value returned by the sizeof function
because its return value is an unsigned Integer type (more details about this
Integer type will be discussed soon).

**The Type specified for a variable determines the range of values that the
variable can store.**

C takes portability(the ability of your program to compile on different kinds of
machines) seriously and actually bothers to tell you what values and ranges are
guaranteed to be safe for each **Type**. In the following sections, you will
learn more about each type and its guaranteed range of values:


### Integer Type
An Integer type variable will store integer constants. `int` is the keyword
that is used to specify the Integer type.

An integer constant consist of a sequence of one or more digits. A minus sign
before the sequence indicates that the value is negative. No embedded spaces are
permitted between the digits, and values larger than 999 cannot be expressed
using commas. C allows integer constants to be written in decimal notation (base
10), octal notation (base 8), or hexadecimal notation (base 16).

**Decimal** integer constant contain digits between 0 and 9. They must not begin
with a zero:
```C
/* examples of valid integer constant */
-10
255
11000
```
**Octal** integer constants contain only digits between 0 and 7. They must begin
with a zero:
```C
/* example of valid octal integer constants */
017
0377
0777777
```
**Hexidecimal** integer constants contain digits between 0 and 9 and letter between
a and f. They must begin with 0x:
```C
/* examples of valid hexadecimal integer constant */
0xff
0xfF
0x1A
0xAB
```
> Remember that integers constants are always stored in binary regardless of
> what notation we have used to express them in our codes. These notation are
> nothing more than an alternative way to write numbers.

An Integer type Variable can be declared as one of two forms; **signed** or
**unsigned**. By default, a Variable declared with the keyword `int` is a **signed**
Integer type Variable. This means it can store either negative or positive
Integer constants. To declare an **unsigned** Integer type Variable, we use the
keyword `unsigned int`. An **unsigned** Integer type Variable can only store
positive Integer constants.

For both `signed` and `unsigned` integer types, C provides 3 subtype
flavours to allow us construct an Integer type variable that meets our needs.
The following keywords are used to specify each subtype flavors:

- `short int`
- `unsigned short int`
- `int`
- `unsigned int`
- `long int`
- `unsigned long int`

C allows us to abbreviate the subtype keywords in our codes by dropping the word
`int`. For example, `short int` can be abbreviated to `short` and
`unsigned long int` can be abbreviated to just `long`. Omitting `int` this
way is a widespread practice among C programmers.

The subtype flavour that you specify in a variable's declaration
determines the range of values that can be stored through the variable and its
memory allocation for the variable.

The range of values represented by each of the subtypes varies from one machine
to another. The following table shows the memory allocation for each subtype and
the range of values that they represent on most 64-bit Linux machines:

|Type | Memory allocation | Value range
--- | --- | ---
`short` | 2 bytes | -32,768 to 32,767
`unsigned short` | 2 bytes | 0 to 65,535
`int` | 4 bytes | -2,147,483,648 to 2,147,483,647
`unsigned int` | 4 bytes | 0 to 4,294,967,295
`long` | 8 bytes | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
`unsigned long` | 8 bytes | 0 to 18,446,744,073,709,551,615

#### How to print the value in an Integer type Variable

We use a format specifier to print the value stored in a variable with the
`printf`function.

The following table shows each Integer type subtype and its `printf` format
specifier:
Type | decimal notation `printf` format
		specifier
--- | --- | --- | 
`short` | `%d`
`unsigned short` | `%u`
`int` | `%d`
`unsigned int` | `%u`
`long` | `%`
Use format specifier `%d` with `printf` to print the value in a **signed** Integer type variable.
And use format specifier `%u` with `pri`is the format specifier used to print the value
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


`%lu` is the format specifier used to print the values of `unsigned long int`
variables while `%ld` is used to print the values of `signed long int`
variables. To print the values stored in `unsigned short int` and
`signed short int` variables use the format specifier `%u` and `%d` respectively.

> The return value of most C standard library functions are unsigned long integers.
> Check the earlier code snippet example that used the `sizeof` function to see how to
> print an unsigned integer.




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
aCharConst = 'B'; /* upper-case B */
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
