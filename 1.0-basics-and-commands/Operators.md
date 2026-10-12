# Operators

## Contents
- [`How Operators and math work in bash`](#how-operators-and-math-work-in-bash)
  - [`Operators, operands, and values`](#operators-operands-and-values)
    - [`Operator`](#operator)
    - [`Operand`](#operand)
    - [`Value`](#value)
  - [`Expressions and results`](#expressions-and-results)
    - [`Expression`](#expression)
    - [`Result`](#result)
  - [`Bash operator contexts`](#bash-operator-contexts)
    - [`Arithmetic contexts`](#arithmetic-contexts)
    - [`Conditional tests`](#conditional-tests)
    - [`Shell command operators`](#shell-command-operators)
- [`1. Common Programming Operators`](#1-common-programming-operators)
  - [`1.1 Arithmetic`](#11-arithmetic)
    - [`Addition`](#addition)
    - [`Subtraction (-)`](#subtraction)
    - [`Multiplication (*)`](#multiplication)
    - [`Division (/)`](#division)
    - [`Remainder (Modulus)`](#remainder-modulus)
    - [`Exponentiation`](#exponentiation)
    - [`Increment and Decrement`](#increment-and-decrement)
    - [`Unary Operators`](#unary-operators)
    - [`Bitwise Operators`](#bitwise-operators)
    - [`Bit Shifts`](#bit-shifts)
    - [`Comma Operator`](#comma-operator)
  - [`1.2 Comparison`](#12-comparison)
    - [`Equal to`](#equal-to)
    - [`Not equal to`](#not-equal-to)
    - [`Less than`](#less-than)
    - [`Greater than`](#greater-than)
    - [`Less than or equal to`](#less-than-or-equal-to)
    - [`Greater than or equal to`](#greater-than-or-equal-to)
  - [`1.3 Logical: AND, OR, NOT`](#13-logical-and-or-not)
    - [`AND`](#and)
    - [`OR`](#or)
    - [`NOT`](#not)
  - [`1.4 Assignment`](#14-assignment)
    - [`Basic assignment`](#basic-assignment)
    - [`Compound assignment`](#compound-assignment)
- [`2. Bash Specific Operators`](#2-bash-specific-operators)
  - [`Comparing numbers`](#comparing-numbers)
  - [`Comparing strings`](#comparing-strings)
  - [`Checking strings`](#checking-strings)
  - [`Checking files and directories`](#checking-files-and-directories)
  - [`Matching patterns`](#matching-patterns)
  - [`Matching regular expressions`](#matching-regular-expressions)
  - [`Combining conditions`](#combining-conditions)
  - [`Arithmetic evaluation`](#arithmetic-evaluation)
  - [`Pipes`](#pipes)
  - [`Input and Output Redirection`](#input-and-output-redirection)
  - [`Command Chaining`](#command-chaining)

## How Operators and math work in bash

### Operators, operands, and values

#### Operator
- Meaning: An operator is a symbol that tells Bash what operation to perform.
- Role in an expression: It acts on one or more operands. In `4 + 5`, `+` is the operator, and `4` and `5` are the operands.

- **Math example**: `4 + 5 = 9`

- **Bash example**:
```bash
echo "$((4 + 5))"
# Output: 9
```

#### Operand
- Meaning: An operand is a value that an operator acts on.
- Role in an expression: In `4 + 5`, `4` and `5` are the operands that the `+` operator adds.

- **Math example**: `4 + 5 = 9` (`4` and `5` are the operands.)

- **Bash example**:
```bash
echo "$((4 + 5))"
# Output: 9
```

#### Value
- Meaning: A value is data used in an expression or produced as its result.
- Role in an expression: In `4 + 5 = 9`, `4` and `5` are the input values, and `9` is the result value.

- **Math example**: `4 + 5 = 9` (`9` is the result value.)

- **Bash example**:
```bash
echo "$((4 + 5))"
# Output: 9
```

### Expressions and results

#### Expression
- Meaning: An expression is a combination of values and operators that represents a calculation or condition.
- Role in an expression: Bash evaluates the expression to determine its result.

- **Math example**: `4 + 5` is an expression.

- **Bash example**:
```bash
echo "$((4 + 5))"
# Output: 9
```

#### Result
- Meaning: A result is the value produced when an expression is evaluated.
- Role in an expression: It is the outcome of the calculation or condition represented by the expression.

- **Math example**: The result of `4 + 5` is `9`.

- **Bash example**:
```bash
echo "$((4 + 5))"
# Output: 9
```

### Bash operator contexts
- What a context means: A context is the part of a Bash command where an operator is used, such as in an arithmetic calculation, a conditional test, or between shell commands.

- Why the context matters: Bash interprets symbols according to where they appear. The syntax and behavior can differ between contexts, so the surrounding syntax helps determine what an operator means.

### Arithmetic contexts
- Purpose: Evaluate arithmetic expressions using integer values.
- Syntax: `$(( expression ))` calculates a value and substitutes it into the command. `(( expression ))` evaluates arithmetic directly as a Bash command.

- Example:
```bash
result=$((4 + 5))
echo "$result"
# Output: 9

count=4
((count += 1))
echo "$count"
# Output: 5
```

Note: Bash arithmetic uses integers and does not calculate floating-point values.

### Conditional tests
- Purpose: Check whether a condition is true or false so a script can choose what to do.
- Syntax: Use `[[ condition ]]` to test a condition. Bash reports a successful test with exit status `0` and an unsuccessful test with exit status `1`.
- Example:
```bash
age=20
if [[ $age -ge 18 ]]; then
  echo "Adult"
fi
# Output: Adult
```

### Shell command operators
- Purpose: Connect commands and control where their input and output come from or go.
- Operators: `|` passes output from one command to another. `<`, `>`, and `>>` redirect input or output. `&&`, `||`, and `;` connect commands.
- Example:
```bash
printf 'hello\n' | wc -l && echo "Count complete"
# Output:
# 1
# Count complete
```



## 1. Common Programming Operators

## 1.1 Arithmetic

### Addition (+)
Addition combines two numbers.

**In math** `4 + 5 = 9`

**In bash**
```bash
echo $((4 + 5))
# Output: 9
```

### Subtraction (-)
Subtraction finds the difference between two numbers.

**In math** `9 - 4 = 5`

**In Bash**
```bash
echo "$((9 - 4))"
# Output: 5
```

### Multiplication (*)
The `*` operator multiplies two numbers.

**In math** `4 * 5 = 20`

**In Bash**
```bash
echo "$((4 * 5))"
# Output: 20
```

### Division (/)
The `/` operator divides one number by another. Bash arithmetic uses integers, so any fractional part is discarded.

**In math** `9 / 2 = 4.5`

**In Bash**
```bash
echo "$((9 / 2))"
# Output: 4
```

### Remainder (Modulus)
The `%` operator returns the remainder left after one integer is divided by another.

**In math** `9 mod 4 = 1`

**In Bash**
```bash
echo "$((9 % 4))"
# Output: 1
```

### Exponentiation
The `**` operator raises the first number to the power of the second.

**In math** `2^3 = 8`

**In Bash**
```bash
echo "$((2 ** 3))"
# Output: 8
```

### Increment and Decrement
The `++` operator increases an integer variable by one, and `--` decreases it by one. Either operator can appear before or after the variable, such as `++count` or `count++`.

**In math** `5 + 1 = 6`; `5 - 1 = 4`

**In Bash**
```bash
count=5
((count++))
echo "$count"
# Output: 6

((count--))
echo "$count"
# Output: 5
```

### Unary Operators
Unary operators act on a single value. In Bash arithmetic, unary `+` leaves a value positive, unary `-` changes its sign, `!` performs logical NOT, and `~` performs bitwise NOT. Increment and decrement operators are covered above.

**In math** Unary `-` changes `5` to `-5`.

**In Bash**
```bash
echo "$((+5))"
# Output: 5

echo "$((-5))"
# Output: -5

echo "$((! 0))"
# Output: 1

echo "$((~0))"
# Output: -1
```

### Bitwise Operators
Bitwise operators work on the individual bits that make up integer values. For example, `6` is `110` in binary and `3` is `011`.

- `&` (AND): A result bit is `1` only when both corresponding bits are `1`.
- `|` (OR): A result bit is `1` when either corresponding bit is `1`.
- `^` (XOR): A result bit is `1` when the corresponding bits are different. In Bash arithmetic, `^` means XOR, not exponentiation.
- `~` (NOT): Flips each bit. This unary operator is also shown in the Unary Operators section.

**In Bash**
```bash
echo "$((6 & 3))"
# Output: 2

echo "$((6 | 3))"
# Output: 7

echo "$((6 ^ 3))"
# Output: 5

echo "$((~0))"
# Output: -1
```

### Bit Shifts
Bit-shift operators move the bits in an integer to the left or right. For positive integers, shifting left multiplies by a power of two, while shifting right divides by a power of two and discards any remainder.

- `<<` (Left Shift): Moves the bits to the left.
- `>>` (Right Shift): Moves the bits to the right.

**In math** `1 * 2^3 = 8`; `8 / 2^2 = 2`

**In Bash**
```bash
echo "$((1 << 3))"
# Output: 8

echo "$((8 >> 2))"
# Output: 2
```

### Comma Operator
The comma operator evaluates arithmetic expressions from left to right. The value of the final expression becomes the result.

**In Bash**
```bash
echo "$((2 + 3, 4 + 5))"
# Output: 9
```





## 1.2 Comparison

### equal to

### not equal to

### less than

### greater than

### less than or equal to

### greater than or equal to


## 1.3 Logical: AND, OR, NOT

### AND

### OR

### NOT

## 1.4 Assignment

### basic assignment

### compound assignment

## 2. Bash Specific Operators

### comparing numbers

### comparing strings

### checking strings

### checking files and directories

### matching patterns

### matching regular expressions

### combining conditions

### arithmetic evaluation

### Pipes

### Input and Output Redirection

### Command Chaining