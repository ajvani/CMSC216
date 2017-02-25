#Intro
##Preprocessor
- Used to make sure program parts see declarations the need
- Directives start with '#' and don't end it ';'

##Data Types
- char, short int, long int (signed/unsigned)
- float, double
- Pointers (*)
- Array of variable []
- Union {}
- Forgetting to initialize variables might give it a random value

###General Rule For Sizes
```c
sizeof(short) <= sizeof(int) <= sizeof(long)
sizeof(float) <= sizeof(double) <= sizeof(long double)
```

##Arithmetic
- Similar to java, casting exists, does integer division (3/2 == 1)

##Booleans
- 0 is false, anything else is true
- Same logic operators as java (!, &&, ||) and comparisons (<=, >=, ...)
    + Logic operators return 1 (true) or 0 (false)

##Random List of Placeholders
- `%d` = decimal
- `%f` = float
- `%c` = char
- `%s` = string

##Input
- Use `scanf`
- General layout: 

```c
scanf("%_", &var); 
```

- `&` receives memory location
- `scanf` returns the number of values it reads

##Functions
- If functions are defined after `main`, they need to be declared
- Functions cannot be overriden/overloaded

##Scopes
C has two types of scopes: 
- Block Scope: a var declared within a block, {}
- File Scope: a var declared globally

##Memory Layout
| |
|:-----:|
|STACK|
|%%%%|
|%%%%|
|%%%%|
|-----------|
|HEAP|
|-----------|
|DATA|
|-----------|
|TEXT|

- Stack: Local variables/parameters
- Heap: Dynamically allocated memory (variables stay here until deallocated)
- Data: Globals/Statics
- Text: Compiled code and constants

##Linkage
A property of an identifier that determines if multiple declarations of that refer to the same variable.
###Types of Linkage
- None: all declarations of an identifier refer to different entities
- Internal: all declarations of an identifier inside a given file refer to the same entity, but declarations accross files refer to different entities
- External: all declarations refer to the same entities (Default)

##Static
- `static` function means internal usage only. You can only use it inside the same file. 
- `static` variable also means internal usage only. 
By default, it can be used anywhere. 

##Enumerated Types
```c
enum Suit {
    SPADES, HEARTS, DIAMONDS=42, CLUBS
}

enum Suit suit1 = SPADES; 
```

##Implicit Type Conversion
Arithmetic operators require their operands to be of the same type to perform the operation 

`int` is actually the "smallest" type used. 
Heirarchy of types: 
- Floating point numbers over integers
- Wide over small
- Unsigned over signed

##Pointers
- Pointer is memory address reference
- Pointer variabls are variables whose value is equal to the address
- Pointers perform manipulation of memory by accessing items at the address
- All pointer variables have the same size

```c
int i = 6; 
int *p = &i;

   Memory|Address
i +------+------+
  | 6    | 1084 | 
  +------+------+
p +------+------+
  | 1084 | 1088 | 
  +------+------+
```

Example: 
```c
int i = 8; 
int *p;
p = &i;
printf("%d %d \n", *p, *(&i)); // prints 6 6

*p = 200; // would change the value of i
```

Using pointers to swap: 
```c
void swap(int *a, int *b) {
    int tmp = *a; 
    *a = *b; 
    *b = tmp;
}
```
Without pointers, the swap would only occur with the local variabls of the function. The use of pointers allows us to access memory outside the scope of a certain code block.

- If you use a gabage pointer (i.e. a pointer to null), you get a Seg Fault

##Arrays
- Elements are next to each other in memory
- No length operator

```c
#define ARRAY_LENGTH 3
int main() {
    int a[ARRAY_LENGTH] = {10, 20, 30};
}
```

- Global arrays are initialized to 0, and are garbage in a function
- If you initialize an array with less elemnts, then the rest of the elements are initialized to 0

###2D Arrays
- Next to each other in memory
- `int b[rows][cols] = {{0}, {0}}` is a 2D array of 0s
- `char p[2][3]` is either a 2D array of chars or 1D array of strings
- `strcpy(p[0], "Mike"` does this: 

|  | 0 | 1 | 2 |
|:---:|:---:|:---:|:---:| 
| 0 | M | i | k | 
| 2 | e | \0 |  | 

##Constants
- `const` = variable can't be changed
- Something confusing: 

```c
    const int *p1; 
    int *const p2; 
    const int *const p3; 
```

- Cannot change the value of whatever p1 is pointing to, but you can change what p1 is pointing to. 
- Cannot change what p2 is pointing to, but can change the value of whatever it is pointing to. 
- Cannot change what p3 is pointing to, nor can you change the value of what p3 is pointing to

##Generic Pointers
- `void *` can point to any type
- Cannot dereference `void *`
    + Need to cast or redefine to a real pointer type
    + Good for parameters in functions

##Pointers to pointers
- Useful in function parameters

```c
int i = 4, j = 6; 
int *p = &i;
int **r = &p; 
```

- r points to p which points to i
- Can dereference r
    + `**r = 9` -> makes i = 9
    + `*r = &j` -> makes p point to j

##Pointers and Arrays
```c
in a[3] = {10, 20, 30};
int *p = a; 
```
Some cool things about this: 
- You can dereference a
    + `*(a+1)` is equivalent to `a[1]`
- Pointers are literally the same as arrays
    + `p[0]` is equivalent to `a[0]`, `p[1]` is equivalent to `a[1]` ... 

##Strings
- Literally just an array of char with a '\0' at the end
- `scanf` reads strings with '%s'
    + Does not read spaces, registers with newline
- `<string.h>` has lots of string functions
    + `strlen(_string_)`
    + `strcmp(s1,s2)` == 0 if `s1` and `s2` are same
    + `strcpy(char *dest, const char *str)`

Something something:
```c
char *str1 = "CHERRY"; 
char *str2 = "MILKSHAKE"; 
strcpy(str2, str1)
```
That does this to str2: 

From: 

| M | I | L | K | S | H | A | K | E | \0 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|

To: 

| C | H | E | R | R | Y | \0 | K | E | \0 |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|

##Structures
`typedef type aliasName;` -> `typedef double Dollars`
- Lets you initialize var to `Dollars`
- Different from `#define` because its not in the processor

```c
struct tag {
    member-list;
};
```

- Declare with `struct tag var_name` OR DO THIS

```c
typdef struct tag {
    member-list; 
}; Name
```

- That lets you declare with `Name var_name`
- You can declare the member list with `Name var_name = {member1, member2, ...}`
    + Undeclared members will be set to 0
- Cannot set `struct1 = struct2`

If we have: 
```c
struct pixel {
    int num; 
    char color; 
};

int function1(struct pixel *p) {
    (*p).num = 8;
}

int function2(struct pixel *p) { 
    p->num - 8; 
}
```

- `function1` and `function2` do the same thing
















