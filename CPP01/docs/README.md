# CPP01

## About

**CPP01** is the second module of the 42 C++ curriculum and focuses on deeper exploration of Object-Oriented Programming (OOP) concepts in C++.

In this module, the goal is to understand **memory allocation, pointers and references, and how objects behave** in different contexts.

Through several exercises, this module reinforces good programming practices and introduces tools that are essential for writing efficient and maintainable C++ code.

## 📂 Project Structure

```bash
CPP01
├── Docs
│   └── en.subject.pdf
│
├── ex00
│   ├── include
│   │   └── Zombie.hpp
│   ├── src
│   │   ├── Zombie.cpp
│   │   ├── newZombie.cpp
│   │   └── randomChump.cpp
│   ├── Makefile
│   └── main.cpp
│
├── ex01
│   ├── include
│   │   └── Zombie.hpp
│   ├── src
│   │   ├── Zombie.cpp
│   │   └── zombieHorde.cpp
│   ├── Makefile
│   └── main.cpp
│
├── ex02
│   ├── include
│   │   └── Brain.hpp
│   ├── src
│   │   └── Brain.cpp
│   ├── Makefile
│   └── main.cpp
│
├── ex03
│   ├── include
│   │   ├── Weapon.hpp
│   │   ├── HumanA.hpp
│   │   └── HumanB.hpp
│   ├── src
│   │   ├── Weapon.cpp
│   │   ├── HumanA.cpp
│   │   └── HumanB.cpp
│   ├── Makefile
│   └── main.cpp
│
├── ex04
│   ├── include
│   │   └── Replace.hpp
│   ├── src
│   │   └── Replace.cpp
│   ├── Makefile
│   └── main.cpp
│
├── ex05
│   ├── include
│   │   └── Harl.hpp
│   ├── src
│   │   └── Harl.cpp
│   ├── Makefile
│   └── main.cpp
│
├── ex06
│   ├── include
│   │   └── Harl.hpp
│   ├── src
│   │   └── Harl.cpp
│   ├── Makefile
│   └── main.cpp
```

---

## Exercise Summaries
| Exercise | Topic                  |
| -------- | ---------------------- |
| ex00     | Stack vs Heap          |
| ex01     | Arrays of Objects      |
| ex02     | Pointers vs References |
| ex03     | Composition            |
| ex04     | File Streams           |
| ex05     | Function Pointers      |
| ex06     | Switch Filtering       |

---

## ex00 — BraiiiiiiinnnzzzZ

This exercise introduces the difference between **stack allocation** and **heap allocation** using a `Zombie` class. 

`Zombie` class stores a `name`, has an `announce()` method, and prints a destruction message in the destructor.

Logic
- `newZombie()` allocates a zombie with new and returns a pointer, which means the zombie lives on the heap until you manually delete it.
- `randomChump()` creates a local `Zombie zombie(name)`; and calls `announce()`;, so that zombie lives on the stack and is destroyed automatically when the function ends

Example Input:
```bash
randomChump("Stack Zombie");

Zombie* zombie1 = newZombie("Heap Zombie");
zombie1->announce();
delete (zombie1);
```

Example Output:
```bash
Stack Zombie: BraiiiiiiinnnzzzZ...
Stack Zombie: destroyed

Heap Zombie: BraiiiiiiinnnzzzZ...
Heap Zombie: destroyed
```

## ex01 — Moar Brainz!
This exercise extends the zombie idea by creating a zombie horde with one allocation. The code allocates an array with new `Zombie[N]`, then fills each element using `setZombie(name)`. 

### Concepts Used
- Dynamic memory allocation
- Arrays of objects
- Memory management with new[] and delete[]
- Object initialization

Logic
- `Zombie` class in this exercise has:
    - a default constructor
    - a named constructor
    - `announce()`
    - `setZombie(std::string name)` for assigning the name after array allocation 

That setter is important because when allocating new `Zombie[N]`, C++ first default-constructs every element, then loop assigns names one by one:
```bash
Zombie* horde = new Zombie[N];

for (int i = 0; i < N; i++)
    horde[i].setZombie(name);
```

### Example Output
```bash
Test Zombie: BraiiiiiiinnnzzzZ...
Test Zombie: BraiiiiiiinnnzzzZ...
Test Zombie: BraiiiiiiinnnzzzZ...
Test Zombie: BraiiiiiiinnnzzzZ...
Test Zombie: BraiiiiiiinnnzzzZ...
Test Zombie: destroyed
Test Zombie: destroyed
Test Zombie: destroyed
Test Zombie: destroyed
Test Zombie: destroyed
```

## ex02 — HI THIS IS BRAIN

This exercise demonstrates the difference between pointers and references.
The program creates a string and then:
- A pointer pointing to the string
- A reference referring to the same string

### Concepts Used
- Pointers
- References
- Memory addresses
-Dereferencing pointers

It prints the memory addresses and values of each to illustrate how they relate.

Logic
```bash
std::string value = "HI THIS IS BRAIN";
std::string* stringPTR = &value;
std::string& stringREF = value;
```

Then it prints:
- the address of the original string: &value
- the address stored inside the pointer: stringPTR
- the address of the reference target: &stringREF

For values, it prints:
- value
- *stringPTR → this is dereferencing the pointer
- stringREF → this is direct reference syntax, no * needed

So this exercise is a very good place to explain:
- stringPTR stores an address
- *stringPTR accesses the value at that address
- stringREF is an alias for value
- &stringREF gives the same address as &value

### Example Output
```bash
PRINT MEMORY ADDRESS
--------------------
Memory address of string variable : 0x...
Memory address held by PTR : 0x...
Memory address held by REF : 0x...

PRINT VALUE
--------------------
Value of string variable : HI THIS IS BRAIN
Value pointed by PTR : HI THIS IS BRAIN
Value pointed by REF : HI THIS IS BRAIN
```

## ex03 — Unnecessary Violence

This exercise introduces references as class members and explores how object relationships work.

### Concepts Used
- References vs pointers
- Composition between classes
- Encapsulation
- Object interaction

Logic
- `Weapon` stores a type string and exposes:
    - `getType()` returning `const std::string&`
    - `setType()` to modify the weapon type

Two classes are implemented:
* `HumanA` → always has a weapon (reference)
* `HumanB` → may or may not have a weapon (pointer)
Both classes can attack using a Weapon object.
This demonstrates the difference between references and pointers inside classes.

`HumanA` stores `Weapon& weapon`;, so it must receive a weapon in the constructor and is always armed:
```c++
HumanA(const std::string& name, Weapon& weaponA);
```

`HumanB`stores `Weapon* weapon`;, initializes it to NULL, and later receives a weapon through `setWeapon()`:
```c++
HumanB(const std::string& name) : name(name), weapon(NULL) {}
void setWeapon(Weapon& weaponB) { this->weapon = &weaponB; }
```

That means:
- `HumanA` + reference = always has a weapon
- `HumanB` + pointer = may have no weapon yet, so a setter makes sense

 attack() methods also show the syntax difference:

`weapon.getType()` for the reference in `HumanA`
- `weapon.getType()` for the reference in `HumanA`
- `weapon->getType()` for the pointer in `HumanB`


### Example Output
```bash
Bob attacks with their club
Jim attacks with their club
Jim attacks with their crued spiked club
```

## ex04 — Sed Is For Losers

This exercise implements a small file processing program that replaces occurrences of a string within a file.

### Concepts Used
* File input/output (std::ifstream, std::ofstream)
* String manipulation
* Error handling
* Working with program arguments

The program:
* Takes a filename and two strings (s1, s2)
* Reads the file content
* Replaces all occurrences of s1 with s2
* Writes the result into a new file with .replace appended

Logic
- checks for exactly 3 arguments after the executable name
- rejects an empty s1
- opens the input file
- creates filename + ".replace"
- reads line by line with `std::getline`
- finds every occurrence of s1
- replaces it by using `erase()` and `insert()` instead of `std::string::replace()`

Replacement loop is the core logic of the exercise
```c++
index = line.find(s1, index);
line.erase(index, s1.length());
line.insert(index, s2);
index += s2.length();
```

### Input Example
```bash
./replace file.txt hello world
```

### Output Example
- Creates: ```file.txt.replace```
- with all "hello" replaced by "world".

## ex05 — Harl 2.0
This exercise introduces function pointers and structured logging behavior.
A Harl class is implemented that can output different complaint messages depending on a given log level.

### Available levels:
- DEBUG
- INFO
- WARNING
- ERROR

### Concepts Used
- Member function pointers
- Encapsulation
- Conditional logic
- String comparison

Logic
Harl class has four private methods:
- debug()
- info()
- warning()
- error()

The interesting part is `complain(std::string level)` implementation. It uses:
- an array of level strings
- an array of member function pointers:
```c++
  void (Harl::*harl_function[])() = {
    &Harl::debug,
    &Harl::info,
    &Harl::warning,
    &Harl::error
};
```

Then it loops through the levels and calls the matching member function with:
```c++
(this->*harl_function[i])();
```


Example Input
```bash
./harl DEBUG
```

Example Output
```bash
DEBUG : I love having extra sauce for my burger.
I really do!
INFO : I cannot believe adding extra sauce costs more money.
WARNING : I think I deserve to have some extra sauce for free.
ERROR : This is unacceptable! I want to speak to the manager now.
Invalid Level
```

