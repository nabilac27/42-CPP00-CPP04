# CPP00

## About

**CPP00** is the first module of the 42 C++ curriculum and introduces the basics of **C++ programming** and **Object-Oriented Programming (OOP)**.  

In this module, the focus is on understanding how C++ differs from C while learning fundamental concepts such as **classes, objects, member functions, constructors, and destructors**. The exercises also emphasize writing structured and modular code using the **C++98 standard**. 


## 📂 Project Structure

```bash
42-CPP00
├── docs
│   └── en.subject.pdf
│   └── en.README.md
├── ex00
│   ├── Makefile
│   └── megaphone.cpp
├── ex01
    ├── include
    │   ├── contact.hpp
    │   └── phonebook.hpp
    ├── src
    │   ├── contact.cpp
    │   └── phonebook.cpp
    ├── Makefile
    └── main.cpp
```

## ex00 — Megaphone

This program takes command-line arguments and prints them in **uppercase**.  
If no arguments are provided, it outputs a default loud message.

The goal of this exercise is to introduce basic **C++ syntax**, **standard input/output**, and working with **command-line arguments**.

### Concepts Used
- `std::cout` for console output
- `std::endl` for newline and buffer flush
- Command-line arguments (`argc`, `argv`)
- Basic character manipulation using ASCII values

#### Input Example
```bash
./megaphone hello world
```

#### Output Example
```bash
HELLO WORLD
```

## ex01 — PhoneBook

This exercise implements a simple **PhoneBook** application using **classes** in C++.  
The program allows the user to **add**, **search**, and **display** contacts through an interactive command-line interface.

### Features
- Stores up to **8 contacts**
- Each contact contains:
  - First name
  - Last name
  - Nickname
  - Phone number
  - Darkest secret
- Prevents empty fields when adding a contact
- Validates that the phone number contains **digits only**
- Displays contacts in a formatted table
- Allows searching by index to show full contact details

### Concepts Used
- Classes and objects
- Private attributes and public member functions
- Header files and source file separation
- `std::string`
- `std::getline`
- Formatted output with `std::setw`
- Input validation

---

### Input Example
```bash
ADD
John
Doe
JD
123456789
Loves pizza
SEARCH
0
```

### Output Exampple
```bash
=========================================
                 PHONEBOOK
=========================================

Enter a command (ADD, SEARCH, EXIT):

First Name     : John
Last Name      : Doe
Nickname       : JD
Phone Number   : 123456789
Darkest Secret : Loves pizza

Contact Added

Enter a command (ADD, SEARCH, EXIT):

-----------------------------------------
            PHONEBOOK SEARCH
-----------------------------------------

     Index|First Name| Last Name|  Nickname
--------------------------------------------
         0|      John|       Doe|        JD

Enter index to view contact information: 0

-----------------------------------------
              CONTACT INFO
-----------------------------------------
First Name     : John
Last Name      : Doe
Nickname       : JD
Phone Number   : 123456789
Darkest Secret : Loves pizza
```
