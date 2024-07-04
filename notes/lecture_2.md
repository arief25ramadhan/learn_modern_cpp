# Lecture 2: Core C++

A C++ program is a sequence of text files (typically header and source files) that contains declarations. They undergo translation to become an executable program, which is executed when the C++ implementation calls its main function.


### 1.1. C++ Keyword
Certain words in a C++ program have special meaning, and these are known as keywords. Others can be used as identifiers. Comments are ignored during translation. Certain characters in the program have to be represented with escape characters/sequences/

```
const, auto, friend, false // C++ keywords
// comment
/*
comment block
*/
"Hello C++ \n"; ///  "\n" is an escape character

```

### 1.2. C++ Entities

The entities of a C++ program are values, objects, references, functions, enumerators, types, class members, templates, template specializations, namespaces. Preprocessor macros are not C++ entities.

```
3.5f; //value entity
std::string str1; //object entity
namespace std; //namespace entity
void MyFunc(); //function entity
const int& a = b; //reference entity
enum MyEnum {}; //enum entity
#define UGLY_MACRO(X) // NOT a C++ entity

```

### 1.3. C++ Declarations

Declarations may introduce entities, associate them with names and define their properties. The declarations that define all properties required to use an entity are definitions.

```
int foo; // introduce entity named foo
void MyFunc(); // introduce entity named MyFunc

// Introduce entity named GreatFunction
// Also, this is a definition of "GreatFunction"
void GreatFunction(){
  //do stuff
}

```

### 1.4. C++ Definitions

Definitions of functions usually include sequences of statements, some of which include expressions, which specify the computations to be performed by the program.

```
// Function Definition
void MyFunction(){
  int a; //statement
  int b; //statement
  int c = a + b; //a + b is an expression
}

```

Notes: Every C++ statements ends with a semicolon (;).

### 1.5. C++ Names

Names encountered in a program are associated with the declarations that introduced them. Each name is only valid within a part of the program called its scope.

```
int my_variable ; //"my_variable" is the name

{             //{<-this defines a new scope
float var_fl; // var_f is valid within this scope
}             //}<-this defines end of the scope

var_fl; //Error, var_fl outside its scope

int var_fl; //Valid, var_fl not declared
```

### 1.6. C++ Variables

Variables is a type of C++ entities. Declared objects and declared references are variables, except for non-static data members.

```
int foo; // variable
bool know_stuff ; // also , variable

MyType my_var; // variable
MyType :: var; // static data member , variable
MyType . data_member ; // non-static data member, not a variable

```