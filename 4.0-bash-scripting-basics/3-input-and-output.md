# 3 - Input and Output

## Contents

- [`Printing output`](#printing-output)
  - [`echo`](#echo)
- [`Reading input`](#reading-input)
  - [`Capturing user input`](#capturing-user-input)

## Printing output

### echo
- What it is: A built-in shell command used to print text or variables to terminal standard output, automatically appending a newline character by default.
- Why it matters: It is the most common and straightforward way to display messages, debug variables, or output data during script execution.

- Example:
```bash
# Basic text output
echo "Hello, World!"

# Printing a variable
GREETINGS="Welcome"
echo "$GREETINGS, user!"

# Suppressing the trailing newline using -n
echo -n "Loading... "
```

## Reading input

### Capturing user input and options
- What it is: A way to use `read` command flags to control how user input is prompted, secured, timed, and parsed.
- Why it matters: Handling standard input often requires constraints like hidden passwords, timeouts, or character limits to build interactive scripts that handle user input smoothly.
- Option reference:
  - `-p prompt`: Displays a prompt string without a trailing newline before reading input.
  - `-s`: Silent mode; hides typed characters on the screen, which is essential for capturing passwords or sensitive data.
  - `-t seconds`: Sets a timeout limit, causing the read command to fail if input isn't provided in time.
  - `-n count`: Returns immediately after reading a specific number of characters instead of waiting for enter.
  - `-a array`: Assigns each space-separated word of the input into an indexed array.

- Example:
```bash
#!/usr/bin/env bash

# Prompt with a timeout and hidden input for a password
read -p "Username: " user
read -sp "Password (times out in 5s): " -t 5 pass
echo -e "\nWelcome, $user!"
```