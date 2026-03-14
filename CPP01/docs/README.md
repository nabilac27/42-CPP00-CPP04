# CPP01

## About

**CPP01** is the second module of the 42 C++ curriculum and focuses on deeper exploration of Object-Oriented Programming (OOP) concepts in C++.

In this module, the goal is to understand **memory allocation, pointers and references, and how objects behave** in different contexts.

Through several exercises, this module reinforces good programming practices and introduces tools that are essential for writing efficient and maintainable C++ code.

## 📂 Project Structure

```bash

```

---

## ex00 — BraiiiiiiinnnzzzZ

This exercise introduces dynamic memory allocation and the difference between stack and heap memory.
A Zombie class is created with a name attribute and a function that announces the zombie. 
The exercise demonstrates when and how memory must be manually managed.

Two functions are implemented:
- `newZombie()` → creates a zombie on the heap
- `randomChump()` → creates a zombie on the stack

### Concepts Used
- Classes and objects
- Constructors and destructors
- Heap vs stack memory
- new and delete
- Basic class design

Example Output
```bash
Zombie Foo: BraiiiiiiinnnzzzZ...
Zombie Bar: BraiiiiiiinnnzzzZ...
```

## ex01 — Moar Brainz!

This exercise builds on the previous one by creating a zombie horde.
A function zombieHorde() dynamically allocates an array of zombies and initializes them with the same name.
The program then demonstrates how to iterate through the horde and make each zombie announce itself.

### Concepts Used
- Dynamic memory allocation
- Arrays of objects
- Memory management with new[] and delete[]
- Object initialization

### Example Output
```bash
Zombie Horde1: BraiiiiiiinnnzzzZ...
Zombie Horde1: BraiiiiiiinnnzzzZ...
Zombie Horde1: BraiiiiiiinnnzzzZ...
```

## ex02 — HI THIS IS BRAIN

This exercise demonstrates the difference between pointers and references.
The program creates a string and then:
- A pointer pointing to the string
- A reference referring to the same string

It prints the memory addresses and values of each to illustrate how they relate.

### Concepts Used
- Pointers
- References
- Memory addresses
-Dereferencing pointers

### Example Output
```bash
Memory address of string      : 0x7ffeedc
Memory address held by pointer: 0x7ffeedc
Memory address of reference   : 0x7ffeedc

Value of string      : HI THIS IS BRAIN
Value pointed to     : HI THIS IS BRAIN
Value referenced     : HI THIS IS BRAIN
```

## ex03 — Unnecessary Violence

This exercise introduces references as class members and explores how object relationships work.

Two classes are implemented:
* HumanA → always has a weapon (reference)
* HumanB → may or may not have a weapon (pointer)

Both classes can attack using a Weapon object.
This demonstrates the difference between references and pointers inside classes.

### Concepts Used
- References vs pointers
- Composition between classes
- Encapsulation
- Object interaction

```bash
Example Output
Bob attacks with their club
Jim attacks with their club
Jim attacks with their crued spiked club
```

## ex04 — Sed Is For Losers

This exercise implements a small file processing program that replaces occurrences of a string within a file.

The program:
* Takes a filename and two strings (s1, s2)
* Reads the file content
* Replaces all occurrences of s1 with s2
* Writes the result into a new file with .replace appended

### Concepts Used
* File input/output (std::ifstream, std::ofstream)
* String manipulation
* Error handling
* Working with program arguments

Input Example
```bash
./replace file.txt hello world
```

Output Example
- Creates: ```file.txt.replace```
- with all "hello" replaced by "world".

## ex05 — Harl 2.0
This exercise introduces function pointers and structured logging behavior.
A Harl class is implemented that can output different complaint messages depending on a given log level.

Available levels:
- DEBUG
- INFO
- WARNING
- ERROR

### Concepts Used
- Member function pointers
- Encapsulation
- Conditional logic
- String comparison

Example Input
```bash
./harl DEBUG
```

Example Output
```bash
[ DEBUG ]
I love having extra bacon for my burger!
```

## ex06 — Harl Filter

This exercise extends the previous one by implementing a complaint filtering system.

Depending on the input log level, the program prints only the relevant messages and those above it in severity.

### Concepts Used
- Switch statements
- Log filtering
- Control flow
- Reusing class behavior

Example Input
```bash
./harlFilter WARNING
```

Example Output
```bash
[ WARNING ]
I think I deserve some extra bacon for free.

[ ERROR ]
This is unacceptable! I want to speak to the manager now.
```
