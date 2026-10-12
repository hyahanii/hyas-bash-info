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

---

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



---

## 1. Common Programming Operators

---

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





---

## 1.2 Comparison

### Equal to
An equality comparison checks whether two values are the same. In Bash, use `-eq` to compare numbers and `==` inside `[[ ... ]]` to compare strings.

**In math** `5 = 5`

**In Bash**
```bash
if [[ 5 -eq 5 ]]; then
  echo "The numbers are equal"
fi
# Output: The numbers are equal

if [[ "cat" == "cat" ]]; then
  echo "The strings are equal"
fi
# Output: The strings are equal
```

### Not equal to
A not-equal comparison checks whether two values are different. In Bash, use `-ne` to compare numbers and `!=` inside `[[ ... ]]` to compare strings.

**In math** `5 != 4`

**In Bash**
```bash
if [[ 5 -ne 4 ]]; then
  echo "The numbers are different"
fi
# Output: The numbers are different

if [[ "cat" != "dog" ]]; then
  echo "The strings are different"
fi
# Output: The strings are different
```

### Less than
A less-than comparison checks whether the left value is smaller or comes before the right value. In Bash, use `-lt` to compare numbers and `<` inside `[[ ... ]]` to compare strings in lexicographic order.

**In math** `3 < 5`

**In Bash**
```bash
if [[ 3 -lt 5 ]]; then
  echo "3 is less than 5"
fi
# Output: 3 is less than 5

if [[ "apple" < "banana" ]]; then
  echo "apple comes before banana"
fi
# Output: apple comes before banana
```

### Greater than
A greater-than comparison checks whether the left value is larger than the right value. In Bash, use `-gt` for numbers and `>` inside `[[ ... ]]` for strings in lexicographic order.

**In math** `8 > 5`

**In Bash**
```bash
if [[ 8 -gt 5 ]]; then
  echo "8 is greater than 5"
fi
# Output: 8 is greater than 5

if [[ "banana" > "apple" ]]; then
  echo "banana comes after apple"
fi
# Output: banana comes after apple
```

### Less than or equal to
A less-than-or-equal comparison checks whether the left number is smaller than or equal to the right number. In Bash, use `-le` to compare numbers.

**In math** `5 <= 5`; `3 <= 5`

**In Bash**
```bash
if [[ 5 -le 5 ]]; then
  echo "5 is less than or equal to 5"
fi
# Output: 5 is less than or equal to 5
```

### Greater than or equal to
A greater-than-or-equal comparison checks whether the left number is larger than or equal to the right number. In Bash, use `-ge` to compare numbers.

**In math** `5 >= 5`; `8 >= 5`

**In Bash**
```bash
if [[ 8 -ge 5 ]]; then
  echo "8 is greater than or equal to 5"
fi
# Output: 8 is greater than or equal to 5
```

Note: Bash's `[[ ... ]]` uses `<` and `>` for string ordering, but has no direct string `<=` or `>=` operators. Those comparisons can be written by combining a string-ordering test with `==`.


---

## 1.3 Logical: AND, OR, NOT

### AND
Logical AND is true only when both conditions are true. In Bash conditional tests, use `&&`.

**In logic** `true AND true = true`

**In Bash**
```bash
if [[ 5 -gt 2 && 8 -gt 3 ]]; then
  echo "Both conditions are true"
fi
# Output: Both conditions are true
```

### OR
Logical OR is true when at least one condition is true. In Bash conditional tests, use `||`.

**In logic** `true OR false = true`

**In Bash**
```bash
if [[ 5 -gt 2 || 8 -lt 3 ]]; then
  echo "At least one condition is true"
fi
# Output: At least one condition is true
```

### NOT
Logical NOT reverses a condition: true becomes false, and false becomes true. In Bash conditional tests, use `!` before the condition.

**In logic** `NOT false = true`

**In Bash**
```bash
if [[ ! 5 -lt 2 ]]; then
  echo "The condition is false, so NOT makes it true"
fi
# Output: The condition is false, so NOT makes it true
```

---

## 1.4 Assignment

### basic assignment
Basic assignment uses `=` to store a value in a variable. In Bash, do not put spaces around `=`.

**In math** `x = 5`

**In Bash**
```bash
name="Alex"
echo "$name"
# Output: Alex
```

### compound assignment
Compound assignment combines an arithmetic operation with assignment, updating a variable using its current value. Common operators are `+=`, `-=`, `*=`, `/=`, `%=`, and `**=`.

**In math** If `count` is `5`, then `count += 3` makes it `8`.

**In Bash**
```bash
count=5
((count += 3))
echo "$count"
# Output: 8

((count *= 2))
echo "$count"
# Output: 16
```

Note: Compound arithmetic assignment is written inside `(( ... ))`; Bash uses integer arithmetic, so division discards any fractional part.

---

## 2. Bash Specific Operators

### comparing numbers
Use these operators inside `[[ ... ]]` to compare integer values:

- `-eq`: Equal to
- `-ne`: Not equal to
- `-gt`: Greater than
- `-lt`: Less than
- `-ge`: Greater than or equal to
- `-le`: Less than or equal to

**In Bash**
```bash
first=5
second=3

if [[ $first -gt $second ]]; then
  echo "$first is greater than $second"
fi
# Output: 5 is greater than 3
```

Note: These operators compare integers, not floating-point numbers. For example, use `-eq` for numeric equality; use `==` inside `[[ ... ]]` when comparing strings.

### comparing strings
Use these operators inside `[[ ... ]]` to compare string contents:

- `==`: Equal to
- `!=`: Not equal to
- `<`: Comes before in lexicographic order
- `>`: Comes after in lexicographic order

**In Bash**
```bash
first="apple"
second="banana"

if [[ "$first" == "apple" ]]; then
  echo "The strings are equal"
fi
# Output: The strings are equal

if [[ "$first" != "$second" ]]; then
  echo "The strings are different"
fi
# Output: The strings are different

if [[ "$first" < "$second" ]]; then
  echo "$first comes before $second"
fi
# Output: apple comes before banana
```

Note: These compare text, not numeric values. For example, `"10" < "2"` is true as a string comparison because the first character `1` comes before `2`. Use numeric operators such as `-lt` when comparing numbers.

### checking strings
Use these tests inside `[[ ... ]]` to check whether a string is empty or contains text:

- `-z`: True if the string has zero length (is empty).
- `-n`: True if the string has non-zero length (is not empty).

**In Bash**
```bash
name=""
if [[ -z "$name" ]]; then
  echo "The string is empty"
fi
# Output: The string is empty

name="Alex"
if [[ -n "$name" ]]; then
  echo "The string is not empty"
fi
# Output: The string is not empty
```

Note: Quoting the variable expansion, as in `"$name"`, keeps the test reliable when the value contains spaces or is empty.

### checking files and directories
Use these tests inside `[[ ... ]]` to check a path:

- `-e`: The path exists.
- `-f`: The path exists and is a regular file.
- `-d`: The path exists and is a directory.
- `-r`: The path is readable.
- `-w`: The path is writable.
- `-x`: The path is executable, or is a searchable directory.
- `-s`: The path exists and is not empty.

Put `!` before a test to check that it is false, such as `! -e` for a path that does not exist.

**In Bash**
```bash
path="notes.txt"

if [[ -e "$path" ]]; then
  echo "The path exists"
fi

if [[ -f "$path" ]]; then
  echo "It is a regular file"
elif [[ -d "$path" ]]; then
  echo "It is a directory"
fi
```

Note: The example prints a message only when the corresponding test passes. Quote path variables so paths containing spaces are handled correctly.

### matching patterns
Inside `[[ ... ]]`, `==` checks whether a string matches a shell pattern. `!=` checks whether it does not match. Common pattern characters include:

- `*`: Matches any number of characters, including none.
- `?`: Matches exactly one character.
- `[abc]`: Matches one character from the listed characters. A range such as `[0-9]` matches one digit.

**In Bash**
```bash
filename="report.txt"

if [[ "$filename" == *.txt ]]; then
  echo "This is a text file"
fi
# Output: This is a text file
```

Note: Quote the string being checked, but leave the pattern unquoted when you want its wildcard characters to work. Quoting the pattern makes those characters literal.

### matching regular expressions
Inside `[[ ... ]]`, the `=~` operator checks whether a string matches a regular expression. Bash uses POSIX extended regular expression syntax.

**In Bash**
```bash
value="abc123"

if [[ "$value" =~ ^[[:alpha:]]+[[:digit:]]+$ ]]; then
  echo "The value has letters followed by digits"
fi
# Output: The value has letters followed by digits
```

Here, `^` matches the start of the string, `$` matches the end, and `+` means one or more of the preceding character class. Anchoring the pattern this way requires the entire string to match.

Note: Quote the string being checked, but leave the regular expression unquoted so its special characters keep their meaning.

### combining conditions
Inside `[[ ... ]]`, combine tests to check more than one condition:

- `&&` (AND): Both conditions must be true.
- `||` (OR): At least one condition must be true.
- `!` (NOT): Reverses the result of a condition.

**In Bash**
```bash
age=30

if [[ $age -ge 18 && $age -lt 65 ]]; then
  echo "The age is between 18 and 64"
fi
# Output: The age is between 18 and 64

if [[ $age -lt 18 || $age -ge 65 ]]; then
  echo "The age is outside the range"
fi
```

Note: Inside `[[ ... ]]`, `&&` and `||` combine conditions. Between commands, they instead control whether the next command runs; that use is covered under Command Chaining.

### arithmetic evaluation
Bash can evaluate arithmetic expressions directly using arithmetic expansion or arithmetic commands. This is useful for counters, calculations, and numeric checks without needing an external calculator.

- `$(( expression ))`: Expands to the result of the arithmetic expression.
- `(( expression ))`: Evaluates the arithmetic expression directly in Bash.

**In Bash**
```bash
total=$((5 + 7))
echo "$total"
# Output: 12

count=10
((count *= 2))
echo "$count"
# Output: 20
```

You can also use arithmetic evaluation inside a condition:
```bash
if (( 8 > 3 )); then
  echo "8 is greater than 3"
fi
# Output: 8 is greater than 3
```

Note: Bash arithmetic works mainly with integers. This means `echo "$((7 / 2))"` gives `3`, because the fractional part is discarded. For decimal math, use tools like `bc` or `awk`.

### Pipes
A pipe, written as `|`, sends the output of one command into the input of another command. This lets you chain simple commands together to build more powerful workflows.

- `command1 | command2`: Sends the standard output of `command1` to the standard input of `command2`.
- Pipes are useful for filtering, counting, sorting, and processing data in stages.

**In Bash**
```bash
printf 'one\ntwo\nthree\n' | wc -l
# Output: 3
```

This example sends the text from `printf` into `wc -l`, which counts the number of lines.

Another example:
```bash
ls /etc | head
# Output: the first few entries from the /etc directory
```

Note: Pipes connect commands by passing output to input. They do not create files; they only move data from one command to another in memory.

### Input and Output Redirection
Redirection changes where a command reads input from and where it sends output. This is one of the most important Bash features for working with files and pipelines.

- `>`: Sends command output to a file, overwriting the file if it already exists.
- `>>`: Appends output to the end of a file.
- `<`: Reads input from a file instead of from the keyboard or another command.
- `2>`: Sends error output to a file instead of the terminal.

**In Bash**
```bash
echo "hello" > greeting.txt
cat greeting.txt
# Output: hello
```

Appending output:
```bash
echo "first line" > notes.txt
echo "second line" >> notes.txt
cat notes.txt
# Output:
# first line
# second line
```

Reading input from a file:
```bash
wc -l < greeting.txt
# Output: 1
```

Redirecting errors:
```bash
ls /nonexistentfolder 2> errors.txt
cat errors.txt
# Output: an error message from ls
```

Note: Redirection controls where data goes, while pipes control how data moves between commands. Use `>` when you want to overwrite a file and `>>` when you want to keep the existing content and add more.

### Command Chaining
Command chaining lets you run multiple commands in one line. Bash decides when to run the next command based on the operator used.

- `;`: Run the next command regardless of whether the previous one succeeded.
- `&&`: Run the next command only if the previous command succeeded.
- `||`: Run the next command only if the previous command failed.

**In Bash**
```bash
echo "Start"; echo "Done"
# Output:
# Start
# Done
```

Using `&&`:
```bash
mkdir demo && cd demo && pwd
# Output: the path of the demo directory
```

Using `||`:
```bash
ls /missingfolder || echo "Folder not found"
# Output: Folder not found
```

You can also combine chaining with other shell operators:
```bash
printf 'hello\n' | wc -c && echo "Count finished"
# Output:
# 6
# Count finished
```

Note: `&&` is useful for safe command sequences, while `||` is useful for fallback behavior. `;` is the simplest form because it always runs the next command, even if the previous one failed.