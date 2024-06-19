# Lecture 0: The Basics

To watch: 

- [Linux Command Line Pipes and Redirection (youtube.com)](https://www.youtube.com/watch?v=mV_8GbzwZMM)
- [Beginner's Guide to the Bash Terminal](https://www.youtube.com/watch?v=oxuRxtrO2Ag)

## 1. Definition

C++ is a compiled language because it uses a compiler to translate the source code into an object code (machine code). Compilers we can use on Linux:
- Clang (used in our examples)
- GCC

## 2. Why using C++ and linux?

From stackoverflow 2018 developer survey results:
- Over 50 k developers surveyed
- Nearly half of them use Linux
- C++ is the most used systms language (4.5 million users in 2015)
- C++ 11 is a modern language
- All companies want C++ in robotics, autonomous driving, etc.

## 3. C++ History

From **assembly language** that is

<table><thead><tr><th><p><strong>Benefits</strong></p></th><th><p><strong>Drawbacks</strong></p></th></tr><tr><th><ul><li>Unbelievably simple instructions (for the computer)</li></ul></th><th><ul><li>A lot of code to do simple tasks</li></ul></th></tr><tr><th><ul><li>Extremely fast</li></ul></th><th><ul><li>Hard to understand</li></ul></th></tr><tr><th><ul><li>Complete control over your program</li></ul></th><th><ul><li>Extremely unportable</li></ul></th></tr></thead></table>

Problem: Computers only understand assembly language

<strong>Idea</strong>:

- Source code can be written in a more intuitive language
- An additional program can convert it into assembly (compiler)

The invention of **C** in1972, made it easy to write code that was fast, simple, and cross-platform. But it has also its <strong>weakness</strong>:

- No objects or classes
- Difficult to write code that worked generically
- Tedious when writing large programs

In 1983, the first vestiges of **C++** were created by Bjarne Stroustrup. He made the language to have high level features, so it is possible to write code that works generically. The term modern C++ refers to the C++ version since C++11 (2011)

## 4. Design Philosophy of C++

- Multi-paradigm
- Express ideas and intent directly in code
- Safety
- Efficiency
- Abstraction

## 5. Standard input/output channels in Linux

- Single input channel:
    - Stdin: Standard input: channel 0
- Two output channels:
    - Stdout: Standard output: channel 1
    - Stderr: Standard error: channel 2

## 6. Examples

- Every C++ code starts with a `main`
- `main` is a function that returns the error code
- Error code `0` means `OK`
- Error code can be any number in `[1, 255]` that means `error`

```
#include <iostream>

int main(){
    // Comment can be like this for one line
    /*
    or like this for
    multiple line
    */

    // Print hello world
    std::cout << "Hello World!" << std::endl;
    return 0;
}
```

### Include directives
Include direcitves copies the content of `file` into the current file.
Two variants:
- #include `<file>` for system include files
- #include `"file"` for local include files

```
#include "some_file.hpp"
// We can use contents of file "some_file.hpp" now
int main(){
    return 0;
}
```

### I/O streams for simple input and output
- Handle `stdin`, `stdout`, and `stderr`:
    - `std::cin` - maps to `stdin`
    - `std::cout` - maps to `stdout`
    - `std::cerr` - maps to `stderr`
- #include`<iostream>` to use I/O streams
- Part of C++ standard library

```
#include <iostream>

int main(){
    int some_number;
    std::cout << "Please input any number" << std::endl;
    std::cin >> some_number;
    std::cout << "Number: " << some_number << std::endl;
    std::cerr << "Boring error message" << std::endl;
    return 0;
}
```
