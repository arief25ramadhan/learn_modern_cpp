# Lecture 1: Build and Tools

Figure 1 below displays the software development ecosystem. Learning how to understand the ecosystem/tools will help you a lot in programming C++.

<p align="center">
  <img src="sw_dev_ecosystem.png" width="500" title="hover text">
  <br>Figure 1 - Software Development Ecosystem<br>
</p>

## 1. The Compilation Process

### 1.1. Definition

What is a compiler?
- A compiler is basically a program.
- It is in charge of transforming your source code into binary code.
- Binary code such as 011010101 is the language that a computer can understand.

<p align="center">
  <img src="compilation_process.png" width="500" title="hover text">
  <br>Figure 2 - Compilation Process<br>
</p>

The easiest compile commands possible:
- `clang++ main.cpp`
- This will build a program called `a.out` that's ready to run.
- But it will not always be easy.

### 1.2. Compilation Steps
The compiler performs 4 steps to build your code:
1. Pre-process: Remove/ignore all the comments, open all the header files.
2. Compile:  Translates a program written in a specific programming language (C++)into the assembly language code
3. Assembly: Translates our assembly code to the machine code and then stores the result in an object file
4. Link: Combines all external programs (such as libraries and other shared components) with our program to create a final executable

Note that in preprocess we deal with the header file (declaration), while in linking we deal with the libraries/objects (implementation).

<p align="center">
  <img src="compilation_step_by_step.png" width="500" title="hover text">
  <br>Figure 3 - Compilation Step by Step<br>
</p>

### 1.3. Compilation Flags
- There is a lof of flags that can be passed while compiling the code,like: `-std=c++17`, `-o`, etc.
- Enable all warnings, treat them as errors: `-Wall`, `-Wextra`, `-Werror`
- Optimization options: `-O0` for no optimizations (default), `-O3` or `-Ofast` for full optimizations
- Keep debugging symbols: `-g`


## 2. Libraries
What is a library?
- Collection of symbols
- Collection of function implementations

- Libraries: multiple object files that are logically connected
- Types of libraries: 
    - Static: Faster, take a lot of space, become part of the end binary, named `lib*.a` (`.a` stands for archive)
    - Dynamic: Slower, can be copied, referenced by a program, named `lib*.so` (`.so` stands for shared object)

### 2.1. Declaration and Definition
- Function declaration can be separated from the implementation details
- Function declaration sets up an interface:
```
void FuncName(int param);
```
- Function definition holds the implementation of the function that can even be hidden from the user:
```
void FuncName(int param){
    // implementation details.
    cout << "Test this function";
}
```

### 2.2. Header/Source Separation
- Move all declarations to header files (`*.hpp`)
- Implementation goes to `*.cpp`, `*.cc`

```
// some_file.hpp for declaration
Type SomeFunc (...args...);

//some_file.cpp for implementation
Type SomeFunc (...args...){}

// program.cpp where we use SomeFunc
# include "some_file.hpp"
int main(){
  SomeFunc(/*args*/);
  return 0;
}
```

### 2.3. What is Linking?
- The library is a binary object that contains the <strong>compiled implementation</strong> of some methods.
- Linking maps a function declaration to its compiled implementation.
- To use a library we need:
  1. A header file `library_api.h`
  2. The compiled library object `libmylibrary.a`

### 2.4. How to Build Libraries?

1. The folder structure:

```
folder/
  --- tools.hpp
  --- tools.cpp
  --- main.cpp
```

2. Make the files

The header files:

```
//  tools.hpp
#pragma once // Avoid include this header file multiple times
void MakeItSunny();
void MakeItRain();
```

The cpp files:

```
//  tools.cpp
#include "tools.hpp"
#include <iostream>

void MakeItSunny(){
  std::cout << "It's now sunny /n";
}

void MakeItRain(){
  std::cerr << "Not yet implemented /n";
};
```

The main function:

```
//  main.cpp
#include "tools.hpp"

int main(){

  MakeItRain();
  MakeItSunny();
  return 0;
}

```

3. Build the files
- Compile: `c++ -std=c++17 -c tools.cpp -o tools.o`
- Organize modules into libraries: `ar rcs libtools.a tools.o`
- Link libraries when building code: `c++ -std=c++17 main.cpp -L . -ltools -o main`

4. Run the program
Execute: `./main`

## 3. Build Systems

- Building by hand is hard
- 4 commands to build a simple hello world example with 2 symbols.
- How does it scales on big projects?
- Impossible to maintain
- Build systems to the rescue!

### 3.1. What are Build Systems?
- Tools to automate the build process of projects.
- They began as `shell` scripts, then turn into `MakeFiles`, and now into MetaBuild Systems like `CMake`.
- `CMake` is not a build system, it is a build system generator. You need to use an actual build system like `Make` or `Ninja`.

### 3.2. What I wish I could write
Replace this build commands:
1. `c++ -std=c++17 -c tools.cpp -o tools.o`
2. `ar rcs libtools.a tools.o`
3. `c++ -std=c++17 main.cpp -L . -ltools -o main`

For a script in the form of:
```
add_library(tools tools.cpp)
add_executable(main main.cpp)
target_link_libraries(main tools)
```

Use CMake to simplify the build
- CMake is one of the most popular build tools
- Does not build the code, generate files to feed into a build system
- Cross-platform
- Very powerful, still build receipt is readable

