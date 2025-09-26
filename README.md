# Theory of Computation & Compiler Optimization Project

This repository contains Python implementations for a **Theory of Computation / Compiler Optimization assignment**. It includes:

1. **Optimizer for arithmetic expressions** – Detects redundant computations, dead code, and applies strength reduction.  
2. **Stack Machine Code Generator** – Converts arithmetic expressions into stack machine instructions.  
3. **Regex to DFA Converter** – Converts a given regular expression into a DFA and prints its transition table.  
4. **DFA Validator** – Validates strings against a DFA generated from a regex `(0|1)*01`.

---

## Files

| File | Description |
|------|-------------|
| `optimizer.py` | Optimizer for arithmetic expressions. |
| `codegen.py` | Stack machine code generator. |
| `regex2dfa.py` | Converts regex to DFA and prints aligned DFA table. |
| `dfa_validator.py` | DFA validator for `(0|1)*01` and validates input strings. |
| `requirements.txt` | Python version and dependencies. |
| `.gitignore` | Standard Python gitignore. |
| `LICENSE` | MIT License. |

---

## Part 1: Optimizer (`optimizer.py`)

### Purpose

Detects **redundant computations**, **dead code**, and applies **strength reduction** in arithmetic expressions.

### How It Works

1. **Constant folding**: Evaluates arithmetic expressions with constants.  
2. **Strength reduction & simplification**: Simplifies expressions like `x*1` → `x`, `y+0` → `y`.  
3. **Copy propagation**: Eliminates unnecessary variable assignments (e.g., `y = x`).  

### How to Run

```bash
python optimizer.py
```
*Sample Input*
```
x = 2 * 8
y = x * 1
z = y + 0
```
*Sample Output*
```commandline
Before optimization:
x = 2 * 8
y = x * 1
z = y + 0

After optimization:
x = 16
z = x
```
***
## Part 2: Stack Machine Code Generator (codegen.py)

## Purpose

Translates an **arithmetic expression** (infix notation) into **stack machine instructions.**

## How It Works

1. Converts **infix → postfix** using **Shunting Yard Algorithm.**

2. **Generates stack instructions:** ***PUSH***, **ADD**, **SUB**, **MUL**, **DIV.**

### How to Run
```bash
python codegen.py
```

***Sample Input***
```commandline
(a+b)*c
```

***Sample Output***
```commandline
PUSH a
PUSH b
ADD
PUSH c
MUL
```
***
## Part 3: Regex to DFA (regex2dfa.py)

### Purpose

Converts a regular expression into a deterministic finite automaton (DFA) and prints a transition table.

### How It Works

1. Add **explicit concatenation operators (.).**
2. Convert **regex** → **postfix** (Reverse Polish Notation). 
3. Build **NFA** using **Thompson's construction.** 
4. Convert **NFA** → **DFA** using **subset construction.** 
5. Print **aligned DFA table** with states, transitions, and accepting states.

### How to Run
```bash
python regex2dfa.py
```

***Sample Input***
```commandline
regex = "(a|b)*abb"
```
***Sample Output***
```commandline
Regex: (a|b)*abb
Postfix: ab|*a.b.b.

DFA Transition Table:
State     a      b      Accepting?  
q0        q1     q0     No          
q1        q1     q2     No          
q2        q3     -      No          
q3        -      -      Yes
```
***
## Part 4: DFA Validator (dfa_validator.py)
## Purpose

Uses a **DFA** generated from ```(0|1)*01``` to validate input strings.

### How It Works

1. Converts regex (0|1)*01 → DFA (using the same approach as regex2dfa.py). 
2. Prints aligned DFA table. 
3. Validates strings:
   + Starts at the DFA initial state.
   + Follows transitions for each character. 
   + Reports Accepted / Rejected based on the ending state.

### How to Run
```bash
python dfa_validator.py
```

***Sample Input***
```commandline
strings_to_test = ["1101", "111", "0001"]
```

***Sample Output***
```commandline
Regex: (0|1)*01

DFA Transition Table:
State     0      1      Accepting?  
q0        q1     q0     No          
q1        q1     q2     No          
q2        -      -      Yes         

String validation results:
1101: Accepted
111: Rejected
0001: Accepted
```
***
### Requirements

+ Python 3.7+ (tested on Python 3.11)
+ No external libraries required

 ***
### License

This project is licensed under the **MIT License.** See LICENSE file.
***

### Recommended Usage

+ ```optimizer.py``` → Use for optimizing arithmetic expressions.
+ ```codegen.py``` → Use to generate stack machine instructions from infix expressions.
+ ```regex2dfa.py``` → Use to convert any regex into a DFA and visualize its transition table.
+ ```dfa_validator.py``` → Use to validate strings against a DFA from regex ```(0|1)*01.```#   S e m - 5 - T O C 
