# 3 - Input and Output

## Contents

- [`Printing output`](#printing-output)
  - [`echo`](#echo)
- [`Reading input`](#reading-input)
  - [`Capturing user input`](#capturing-user-input)

## Printing output

### echo
- What it does: Prints text or values to the terminal output.
- Why use it: Useful for displaying messages, testing commands, and showing variable values while debugging scripts.
- How to use it:
```bash
echo "Hello, World!"
# Output:
# Hello, World!
```

- *echo $VAR* (Print a Variable): Displays the current value of a variable.
Example:
```bash
name="Bash"
echo $name
# Output:
# Bash
```

- *echo -e* (Enable Escape Sequences): Allows special characters like `\n` and `\t` to be interpreted.
Example:
```bash
echo -e "Line 1\nLine 2"
# Output:
# Line 1
# Line 2
```

Note: `echo` is one of the most basic debugging tools in Bash. It is often used to confirm that a script reached a certain point or to print variable values.


## Reading input

### Capturing user input and options
- What it is: A way to use `read` command flags to control how user input is prompted, secured, timed, and parsed.
- Why it matters: Handling standard input often requires constraints like hidden passwords, timeouts, or character limits to build interactive scripts that handle user input smoothly.
- Option reference:
  - `-p prompt`: Displays a prompt string without a trailing newline before reading input.
  - `-s`: Silent mode; hides typed characters on the screen, which is essential for capturing passwords or sensitive data.
  - `-t seconds`: Sets a timeout limit, causing the read command to fail if input isn't provided in time.
  - `-n count`: Returns immediately after resading a specific number of characters instead of waiting for enter.
  - `-a array`: Assigns each space-separated word of the input into an indexed array.

- Example:
```bash
#!/usr/bin/env bash

# Prompt with a timeout and hidden input for a password
read -p "Username: " user
read -sp "Password (times out in 5s): " -t 5 pass
echo -e "\nWelcome, $user!"
```