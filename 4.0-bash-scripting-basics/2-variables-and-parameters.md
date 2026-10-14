# 4.0 - Variables and Parameters

## Contents

- [`Variable assignment`](#variable-assignment)
  - [`Syntax and naming rules`](#syntax-and-naming-rules)
- [`Referencing variables`](#referencing-variables)
  - [`Braced vs unbraced expansion`](#braced-vs-unbraced-expansion)
- [`Positional parameters`](#positional-parameters)
  - [`Arguments and counting`](#arguments-and-counting)
- [`Special parameters`](#special-parameters)
  - [`Exit status and argument arrays`](#exit-status-and-argument-arrays)

## Variable assignment

### Syntax and naming rules
- What it is: The mechanism of storing data in a named identifier without using spaces around the assignment operator.
- Why it matters: Bash relies strictly on syntax spacing; adding spaces around the `=` sign causes the shell to misinterpret the variable name as a command.

- Example:
```bash
# Correct assignment
VAR_NAME="value"

# Incorrect (throws command not found error)
VAR_NAME = "value"
```

## Referencing variables

### Braced vs unbraced expansion
- What it is: Accessing the value stored in a variable using the `$` prefix, either directly or wrapped in curly braces.
- Why it matters: Curly braces prevent naming ambiguity when text or characters immediately follow the variable name.

- Example:
```bash
NAME="Bash"
echo "Hello $NAME"
echo "Hello ${NAME}er" # Prevents parsing errors with trailing text
```

## Positional parameters

### Arguments and counting
- What it is: Built-in variables (`$1`, `$2`, etc.) that automatically capture arguments passed to a script or function from the command line, alongside counting utilities (`$#`).
- Why it matters: It enables your scripts to accept dynamic inputs. Beyond single-digit arguments, accessing double-digit indices requires curly braces (e.g., `${10}`) because `$10` is otherwise interpreted as `$1` followed by a literal `0`.

- Example:
```bash
#!/usr/bin/env bash

echo "First argument: $1"
echo "Tenth argument: ${10}" # Required syntax for double-digit positions
echo "Total arguments: $#"
```

## Special parameters

### Exit status and argument arrays
- What it is: Specialized built-in variables that track execution states, process IDs, or provide collections of all passed arguments.
- Why it matters: They are essential for error handling, process tracking, and safely handling multi-word arguments through iteration.
- Parameter reference:
  - `$?`: Exit status of the last executed command
  - `$*`: All positional parameters as a single string
  - `$@`: All positional parameters as separate strings
  - `$$`: Process ID of the current shell or script
  - `$!`: Process ID of the last background job
  - `$#`: Number of positional parameters passed
  - `$0`: Filename of the current script

- Example:
```bash
#!/usr/bin/env bash

# Capture all arguments as separate strings
for arg in "$@"; do
    echo "$arg"
done

# Check exit status of the previous command
echo "Exit code: $?"