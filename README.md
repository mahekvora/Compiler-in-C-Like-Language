# Compiler-for-nanoC
Implemented a compiler for a C-like language in the following 4 steps. 
The subset of C used here is nanoC

* **Step 1** : Lexical Analyzer for nanoC using Flex. The lexical grammar specification is given here.  
* **Step 2** : Parser for nanoC using Bison. The phase structure grammar specification is given in Assignment 3.  
* **Step 3** : Machine-Independent Code Generator for nanoC using syntax-directed translation with Bison. Three-Address (intermediate) Code (TAC) used as target of translation is explained here.  
* **Step 4** : Target Code Generator for nanoC by simple code generation by table lookup. The target processor is taken to be x86 and a subset of its assembly language is presented here for use.  

## Step 1: Lexical Analysis Using Flex

- **Tokenization:**  
  Flex is used to generate lexical analyzers that tokenize source code.  
  It uses pattern-action pairs to identify lexemes based on regular expressions.

- **Regular Expressions:**  
  Token patterns are defined using regular expressions, enabling Flex to recognize various lexical components in the source code.

- **Efficiency & Customization:**  
  Flex-generated analyzers leverage finite automata for efficient tokenization.  
  It supports customization to tailor lexical rules for different programming languages.

---

## Step 2: Parsing Using Bison

- **Syntax Analysis:**  
  Bison creates parsers for analyzing the syntactic structure of source code, based on defined grammar rules.

- **Grammar Rules:**  
  Language syntax is defined using context-free grammar.  
  Bison employs bottom-up LALR parsing (Look-Ahead Left-to-right, Rightmost derivation) to process grammar rules.

- **Actions & Semantics:**  
  Semantic actions are triggered when grammar rules match during parsing.  
  These actions are used to build data structures like the Abstract Syntax Tree (AST).

---

## Step 3: Machine Independent Code Generation

- **Symbol Table Generation:**  
  Maintains symbol information such as names and addresses.  
  Includes global and local symbol tables with operations like `lookup`, `insert`, and `update`.

- **Three-Address Code (TAC) Generation:**  
  Intermediate code is generated in the form of three-address instructions, enabling further translation and optimization.

- **Quad Table Generation:**  
  Uses a structure with fields like `opcode`, `arg1`, `arg2`, and `result`.  
  Functions like `emit()` and `print()` are used to manage and display intermediate code.

---

## Step 4: Target Code Generation

- **Assembly Code Output:**  
  The `target_translator.c` module generates the final `.asm` file.  
  It utilizes data from the Symbol Table and Quad Table to produce assembly-level instructions.
