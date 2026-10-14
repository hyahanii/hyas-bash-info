# 3.0 - Bash-Specific Operators

## Contents

- [`String and file tests`](#string-and-file-tests)
  - [`Checking strings`](#checking-strings)
  - [`Checking files and directories`](#checking-files-and-directories)
- [`Pattern and regex`](#pattern-and-regex)
  - [`Matching patterns`](#matching-patterns)
  - [`Matching regular expressions`](#matching-regular-expressions)
- [`Pipes`](#pipes)
- [`Redirection`](#redirection)
- [`Command chaining`](#command-chaining)
- [`Condition combinations`](#condition-combinations)
  - [`Combining conditions`](#combining-conditions)

---

## Comparing numbers
[[ $A -eq $B ]]  # Equal to ($A == $B)
[[ $A -ne $B ]]  # Not equal to ($A != $B)
[[ $A -gt $B ]]  # Greater than ($A > $B)
[[ $A -lt $B ]]  # Less than ($A < $B)
[[ $A -ge $B ]]  # Greater than or equal to ($A >= $B)
[[ $A -le $B ]]  # Less than or equal to ($A <= $B)

## Comparing strings
[[ "$NAME" == "Alex" ]]  # Strings are identical
[[ "$NAME" != "Alex" ]]  # Strings are NOT identical
[[ -z "$NAME" ]]         # String is empty
[[ -n "$NAME" ]]         # String is not empty

## String and file tests

### Checking strings
- Meaning: Checking string properties such as whether a string is empty (`-z`), non-empty (`-n`), or comparing string values using conditional test constructs like `[[ ... ]]`.
- Role in execution: Used in conditional statements to validate user input, environment variables, or text data before processing.

- Example:
```bash
name="Alice"
if [[ -n "$name" ]]; then
    echo "String is not empty"
fi
# Output: String is not empty
```

### Checking files and directories
- Meaning: Testing file and directory existence or attributes such as whether a path exists (`-e`), is a regular file (`-f`), is a directory (`-d`), or is readable (`-r`)—using conditional test constructs like `[[ ... ]]`.
- Role in execution: Used in conditional statements to verify paths, configuration files, or logs before reading or writing data.

- Example:
```bash
if [[ -d "/var/log" ]]; then
    echo "Directory exists"
fi
# Output: Directory exists
```

---

## Pattern and regex

### Matching patterns
- Meaning: Matching string patterns or wildcards (like `*` and `?`) using the `==` or `=` operator inside conditional test constructs like `[[ ... ]]`.
- Role in execution: Used in conditional statements to check if a string matches a specific glob pattern (e.g., checking file extensions or prefixes).

- Example:
```bash
filename="document.txt"
if [[ "$filename" == *.txt ]]; then
    echo "It is a text file"
fi
# Output: It is a text file
```

### Matching regular expressions
- Meaning: Matching a string against an Extended Regular Expression (ERE) using the `=~` operator inside conditional test constructs like `[[ ... ]]`.
- Role in execution: Used in conditional statements to perform complex pattern matching, validation, and text analysis in Bash.

- Example:
```bash
email="test@example.com"
if [[ "$email" =~ ^[A-Za-z0-9._\%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$ ]]; then 
    echo "Valid email format"
fi
# Output: Valid email format
```

---

## Pipes

## Redirection
- Meaning: Directing the input or output of a command to or from a file instead of the standard terminal streams using operators like `>`, `>>`, and `<`.
- Role in execution: Used to save command outputs to files, append data without overwriting, or feed file contents into commands.

- Example:
```bash
echo "Hello, World!" > output.txt
cat output.txt
# Output: Hello, World!
```

## Command chaining
- Meaning: Running multiple commands sequentially or conditionally on a single line using operators like `;` (sequential), `&&` (conditional AND), and `||` (conditional OR).
- Role in execution: Used to automate workflows, ensuring subsequent commands only run if previous ones succeed or fail appropriately.

- Example:
```bash
mkdir backup && cp data.txt backup/
echo "Backup completed successfully"
# Output: Backup completed successfully
```

---

## Condition combinations

### Combining conditions
- Meaning: Joining multiple conditional expressions together using logical operators (`&&`, `||`) or grouping with parentheses within conditional test constructs like `[[ ... ]]`.
- Role in execution: Used to build complex, multi-variable decision-making logic in shell scripts.

- Example:
```bash
age=20
has_id="true"
if [[ $age -ge 18 && "$has_id" == "true" ]]; then
    echo "Access granted"
fi
# Output: Access granted
```

### Combining conditions
- Meaning: Joining multiple conditional expressions together using logical operators (`&&`, `||`) or grouping with parentheses inside conditional test constructs like `[[ ... ]]`.
- Role in execution: Used to build complex, multi-variable decision-making logic in shell scripts.

- Example:
```bash
age=20
has_id="true"
if [[ $age -ge 18 && "$has_id" == "true" ]]; then
    echo "Access granted"
fi
# Output: Access granted
```