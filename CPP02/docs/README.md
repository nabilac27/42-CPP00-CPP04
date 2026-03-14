# CPP02

## About

**CPP02** is the third module of the 42 C++ curriculum and introduces important concepts related to **operator overloading, fixed-point arithmetic, and the Orthodox Canonical Form** in C++.

In this module, the goal is to understand how classes behave when copied, assigned, or destroyed, and how to properly implement the canonical functions that control object lifecycle.


📂 Project Structure
```bash
CPP02
├── Docs
│   ├── en.subject.pdf
│   └── README.md
│
├── ex00
│   ├── include
│   │   └── Fixed.hpp
│   ├── src
│   │   └── Fixed.cpp
│   ├── Makefile
│   └── main.cpp
│
├── ex01
│   ├── include
│   │   └── Fixed.hpp
│   ├── src
│   │   └── Fixed.cpp
│   ├── Makefile
│   └── main.cpp
│
├── ex02
│   ├── include
│   │   └── Fixed.hpp
│   ├── src
│   │   └── Fixed.cpp
│   ├── Makefile
│   └── main.cpp
│
├── ex03
│   ├── include
│   │   ├── Fixed.hpp
│   │   └── Point.hpp
│   ├── src
│   │   ├── Fixed.cpp
│   │   ├── Point.cpp
│   │   └── bsp.cpp
│   ├── Makefile
│   └── main.cpp
```
---

## ex00 — My First Canonical Class

This exercise introduces the **Orthodox Canonical Form** in C++.

A Fixed class is created by implementing the four canonical functions:
- Default constructor
- Copy constructor
- Copy assignment operator
- Destructor

The class stores a fixed-point value internally as an integer.

Files
```bash
include/Fixed.hpp
src/Fixed.cpp
main.cpp
```

### Concepts Used
- Orthodox Canonical Form
- Constructors and destructors
- Copy constructor
- Copy assignment operator
- Encapsulation

### Example Output
```bash
Default constructor called
Copy constructor called
Copy assignment operator called
Destructor called
```

---

## ex01 — Towards a More Useful Fixed-Point Class

This exercise improves the Fixed class by allowing conversion between:
- integers
- floating-point numbers
- fixed-point representation

Two constructors are added to convert int and float values into fixed-point format.

Files
```bash
include/Fixed.hpp
src/Fixed.cpp
main.cpp
```

### Concepts Used
- Fixed-point arithmetic
- Type conversion
- toFloat() and toInt() methods
- Operator overloading (<<)

### Example Output
```bash
a is 1234.43
b is 10
c is 42.42
d is 10
```

## ex02 — Now We're Talking

This exercise expands the Fixed class by implementing **operator overloading**.

Arithmetic and comparison operators are added so that fixed-point numbers behave like normal numeric types.

### Operators Implemented
Arithmetic:

- +

- - 

- *

- /

Comparison:

- >

- <

- >=

- <=

- ==

- !=

Increment / Decrement:

- ++

- --

### Utility functions:

- min()

- max()

Files
```bash
include/Fixed.hpp
src/Fixed.cpp
main.cpp
```

### Concepts Used
- Operator overloading
- Arithmetic operations
- Increment / decrement operators
- Static member functions

### Example Output
```bash
0
0.00390625
0.0078125
0.0117188
0.015625
```
