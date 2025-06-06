# Simple Programming Language Compiler

A compiler implementation for a simple programming language with support for basic data types, control structures, and functions. This project demonstrates fundamental compiler design concepts including lexical analysis, parsing, and intermediate code generation.

## Overview

This compiler transforms source code written in a custom, simple programming language into Three-Address Code (TAC), an intermediate representation that can be further processed or executed. The implementation includes:

1. **Lexical Analysis**: Tokenizing source code using Flex
2. **Syntax Analysis**: Parsing tokens using Bison to build an abstract syntax tree (AST)
3. **Semantic Analysis**: Type checking and symbol table management
4. **Intermediate Code Generation**: Generating Three-Address Code

## Language Features

The programming language supports:

- **Data Types**: Integer, Boolean, String, and Character
- **Control Structures**: If-else statements and While loops
- **Functions**: Function declarations with parameters and return values
- **I/O Operations**: Basic print and scan operations
- **Expressions**: Arithmetic, logical, and relational expressions with operator precedence
- **Variables**: Variable declarations with optional initialization
- **Comments**: Single-line (`//`) and multi-line (`/* */`) comments

## Project Structure

- `lexer.L`: Flex specification for lexical analysis
- `parser.y`: Bison grammar for parsing
- `ast.h`: Abstract Syntax Tree definitions
- `main.cpp`: Entry point for the compiler

## Getting Started

### Prerequisites

- GCC compiler
- Flex (Fast Lexical Analyzer)
- Bison (Parser Generator)
- Make (Optional, for build automation)

### Building the Compiler

1. Generate the lexer and parser:
   ```bash
   flex -o lexer.yy.c lexer.L
   bison -d parser.y
   ```

2. Compile the compiler:
   ```bash
   g++ -o compiler main.cpp lexer.yy.c parser.tab.c -lfl
   ```

Alternatively, if you have a Makefile:
```bash
make
```

### Usage

1. Run the compiler:
   ```bash
   ./compiler
   ```

2. When prompted, enter the path to your source code file:
   ```
   Input file: your_program.txt
   ```

3. If parsing is successful, the compiler will generate a Three-Address Code (TAC) file with the same name but `.tac` extension:
   ```
   Parsing Done.
   ThreeAC saved in: your_program.tac
   ```

## Language Syntax

### Variable Declaration
```
int x;
bool flag := true;
string message := "Hello, World!";
char letter := 'A';
```

### Control Structures
```
if (x > 0) {
    print(x);
} else {
    print("x is not positive");
}

while (x > 0) {
    x := x - 1;
}
```

### Functions
```
int add(int a, int b) {
    return a + b;
}

void greet(string name) {
    print("Hello, " + name + "!");
}
```

### Main Function
```
int main() {
    int result := add(5, 3);
    print(result);
    return 0;
}
```

### Expressions
```
int a := 5 + 3 * 2;  // Operator precedence is respected
bool b := (a > 10) and (a < 20);
int c := -a;  // Unary minus
```

### I/O Operations
```
print("Enter a number:");
int n;
scan(n);
print("You entered: " + n);
```

## Three-Address Code (TAC)

The compiler generates Three-Address Code as an intermediate representation. Examples:

```
t0 := 3
t1 := 2
t2 := t0 * t1
t3 := 5
t4 := t3 + t2
a := t4
```

## Symbol Table

The compiler maintains a symbol table to track variables and functions, their types, and other attributes. This helps in semantic analysis, such as type checking and ensuring variables are declared before use.

## Error Handling

The compiler provides error messages for various issues:
- Lexical errors (invalid characters)
- Syntax errors (malformed expressions or statements)
- Semantic errors (type mismatches, undeclared variables, etc.)

Error messages include the line number to help locate and fix issues in the source code.

## Limitations and Future Work

- No arrays or complex data structures
- Limited optimization of the generated code
- No support for object-oriented features
- Future extensions could include:
  - Code optimization passes
  - Target code generation (e.g., MIPS or x86 assembly)
  - More advanced language features

## License

[MIT License](LICENSE)

## Acknowledgments

- This project was developed as part of a compiler design course
- Inspired by classic compiler textbooks and resources
