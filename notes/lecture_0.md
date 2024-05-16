# Lecture 0: The Basics

[Modern C++ (Lecture & Tutorials, 2020, Vizzo & Stachniss) - YouTube](https://www.youtube.com/playlist?list=PLgnQpQtFTOGRM59sr3nSL8BmeMZR9GCIA)

To watch: 

- [Linux Command Line Pipes and Redirection (youtube.com)](https://www.youtube.com/watch?v=mV_8GbzwZMM)
- [Beginner's Guide to the Bash Terminal](https://www.youtube.com/watch?v=oxuRxtrO2Ag)

## 1. Why using C++? Why linux

From stackoverflow 2018 developer survey results:
- Over 50 k developers surveyed
- Nearly half of them use Linux
- C++ is the most used systms language (4.5 million users in 2015)
- C++ 11 is a modern language
- All companies want C++ in robotics, autonomous driving, etc.


## 2. C++ History

From **assembly language** that is

<table><thead><tr><th><p><strong>Benefits</strong></p></th><th><p><strong>Drawbacks</strong></p></th></tr><tr><th><ul><li>Unbelievably simple instructions (for the computer)</li></ul></th><th><ul><li>A lost of code to do simple tasks</li></ul></th></tr><tr><th><ul><li>Extremely fast</li></ul></th><th><ul><li>Hard to understand</li></ul></th></tr><tr><th><ul><li>Complete control over your program</li></ul></th><th><ul><li>Extremely unportable</li></ul></th></tr></thead></table>

Problem: Computers only understand assembly language

<strong>Idea</strong>:

- Source code can be written in a more intuitive language
- An additional program can convert it into assembly (compiler)

The invention of **C** in1972, made it easy to write code that was fast, simple, and cross-platform. But it has also its <strong>weakness</strong>:

- No objects or classes
- Difficult to write code that worked generically
- Tedious when writing large programs

In 1983, the first vestiges of **C++** were created by Bjarne Stroustrup. He made the language to have high level features, so it is possible to write code that works generically. The term modern C++ refers to the C++ version since C++11 (2011)

## 3. Design Philosophy of C++

- Multi-paradigm
- Express ideas and intent directly in code
- Safety
- Efficiency
- Abstraction

## 4. Standard input/output channels in Linux

- Single input channel:
    - Stdin: Standard input: channel 0
- Two output channels:
    - Stdout: Standard output: channel 1
    - Stderr: Standard error: channel 2

## 5. Examples

```
#include <iostream>

int main(){
    // Comment
    std::cout << "Hello World!" << std::endl;
    return 0;
}

```