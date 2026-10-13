# 3.0 - Bash Scripting Basics

## Contents

- [`What a Bash script is`](#what-a-bash-script-is)
- [`How Bash scripts work`](#how-bash-scripts-work)
- [`The Shebang (#!/bin/bash)`](#the-shebang-binbash)
- [`Making a script executable`](#making-a-script-executable)
- [`Comments`](#comments)
- [`Variables`](#variables)
  - [`Basic assignment`](#basic-assignment)
  - [`Reading variables`](#reading-variables)
- [`User input (read)`](#user-input-read)
  - [`read`](#read)
- [`Script arguments`](#script-arguments)
- [`Quoting`](#quoting)
- [`Exit status`](#exit-status)
- [`Basic control flow`](#basic-control-flow)
  - [`If statements`](#if-statements)
  - [`If-else statements`](#if-else-statements)
- [`Basic loops`](#basic-loops)
  - [`For loop`](#for-loop)
  - [`While loop`](#while-loop)
- [`Basic functions`](#basic-functions)
- [`Debugging basics`](#debugging-basics)

This chapter introduces the basic building blocks of Bash programming. It is meant to be a gentle, beginner-friendly starting point for writing simple scripts.

---

## What a Bash script is

- What is a Bash script?: A Bash script is a plain text file that contains a series of Bash commands. When you run the script, the shell reads the file line by line and executes each command in order.
- Why it matters: Scripts help automate repetitive tasks, save time, and let you build simple tools without manually typing the same commands over and over.
- Practical use: You can use Bash scripts to create folders, move files, check system status, back up data, or automate setup steps.
- Example layout:

```bash
#!/usr/bin/env bash

echo "Hello, world!"
ls -l
mkdir -p backup
```

A script usually uses the `.sh` extension, but the file itself is still just a normal text file containing commands.

---

## How Bash scripts work

- How do Bash scripts work? A Bash script is just a text file containing commands. When you run it, Bash opens the file and reads it from top to bottom. Each line is treated as a command, and the shell executes those commands in order unless something changes the flow, such as a conditional, loop, or function call.
- Why it matters: Understanding the flow of a script helps you predict what will happen when it runs. It also makes debugging much easier when a script behaves unexpectedly.
- Practical use: You use this idea every time you create a script to automate repetitive tasks, such as creating files, checking folders, or renaming many items at once.
- Example layout:

```bash
#!/usr/bin/env bash

echo "Starting script..."
mkdir -p project
cd project
pwd
```

This script runs in order: it prints a message, creates a folder, moves into it, and then prints the current directory.

### The Shebang (#!/bin/bash)

- What it is: The shebang is the first line of a script. It tells the system which interpreter should run the file. For Bash, it usually looks like `#!/usr/bin/env bash` or `#!/bin/bash`.
- Why it matters: Without the shebang, your operating system may not know how to run the script correctly.
- Practical use: It lets you run the script directly with `./script.sh` instead of typing `bash script.sh` every time.
- Note: The name “hashbang” or “shebang” comes from the two characters `#` and `!` at the start of the line. In Unix-like systems, the kernel or shell sees `#!` and knows to pass the rest of the line to the interpreter. That is why the line is usually written as `#!/usr/bin/env bash`.
- Example layout:

```bash
#!/usr/bin/env bash
echo "Hello from Bash!"
```

`#!/bin/bash` tells the system to run Bash from the specific path `/bin/bash`. `#!/usr/bin/env bash` runs `env`, which searches your `PATH` for Bash and uses the first match. The `env` version works on systems where Bash is installed in a different location; the fixed path is direct but assumes Bash is at `/bin/bash`.

### Making a script executable

- What it does: A script is a text file, and the executable permission lets the system launch it directly as a program.
- Running without execute permission: You can still run a readable script by passing it to Bash with `bash script.sh`. Bash reads the file and runs its commands, so the script itself does not need execute permission for this form. If you try `./script.sh` without execute permission, the system refuses to launch it and usually prints `Permission denied`.

- What `chmod +x` means: `chmod` means “change mode” and is the command used to change file permissions. In `+x`, `+` means “add” and `x` means “execute.” So `chmod +x script.sh` adds execute permission to the script; it does not change the script's contents. With no user class specified, `chmod` applies the change to the owner, group, and other users, subject to the system's permission rules.

- Practical use: Add execute permission when you want to launch the script directly, share it as an executable script, or run it like a command.
- Note: The `./` means “run the file named `script.sh` from the current directory.” It is needed because the current directory is not usually searched for commands automatically. When launched directly, the system uses the script's shebang to choose the interpreter.
- Example:

```bash
ls -l script.sh
# Example: -rw-r--r-- ... script.sh
bash script.sh

chmod +x script.sh
ls -l script.sh
# Example: -rwxr-xr-x ... script.sh
./script.sh
```

In the permission listing, adding `x` marks the file as executable. The letters before `+` can limit who gets that permission: `u` means the owner, `g` means the group, and `o` means other users. For example, `chmod u+x script.sh` adds execute permission only for the owner.

---

## Comments

- What it is: Comments are notes written inside a script that Bash ignores when running the file. They are meant for people reading the script, not for the shell itself.
- Why it matters: Comments make scripts easier to understand, especially when you revisit them later or share them with other people. They help explain what a command is doing without affecting execution.
- Practical use: You use comments to label steps, explain tricky logic, and leave reminders in scripts.
- Example layout:

```bash
#!/usr/bin/env bash

# This script creates a folder and prints a welcome message
mkdir -p my_project

echo "Welcome to my_project!"
```

In this example, the line starting with `#` is a comment, so Bash does not try to execute it.

---

## Variables

- What it is: Variables are names that store values so you can reuse them later in a script. They make scripts easier to write, read, and update.
- Why it matters: Instead of hard-coding the same value repeatedly, you can assign it once and use it anywhere in your script. This is especially useful for names, file paths, settings, and numbers.
- Practical use: You can store a username, a folder path, a message, or a count and then use that value in commands and output.
- Example layout:

```bash
#!/usr/bin/env bash

name="Alice"
folder="~/projects"

echo "Hello, $name!"
mkdir -p "$folder"
```

### Basic assignment
For more information check [`1.4 Assignment`](Operators.md#14-assignment).

- What it is: Basic assignment is when you give a variable a value using `=`.
- Why it matters: Assignment lets the script remember information for later use.
- Practical use: You can store values like a filename, a message, or a number.
- Example layout:

```bash
name="Alice"
count=10
project="demo"
```

### Reading variables

- What it is: Reading a variable means using its value by writing `$variable_name`.
- Why it matters: This lets you reuse the stored value in commands or messages instead of typing it again.
- Practical use: You can print the value, pass it to a command, or compare it with another value.
- Example layout:

```bash
name="Alice"
echo "Welcome back, $name!"
```

---

## User input (read)

- What it is: User input means getting information from the person running the script. In Bash, the `read` command is used to wait for input from the terminal and store it in a variable.
- Why it matters: This allows a script to react to real-time user choices, names, file names, or values instead of always doing the same thing.
- Practical use: You can ask for a username, a filename, a confirmation, or a number before continuing with the script.
- Example layout:

```bash
#!/usr/bin/env bash

read -p "Enter your name: " name
echo "Hello, $name!"
```

### read

- What it does: `read` waits for input, then stores it in a variable. By default, it reads until the user presses Enter.
- Basic syntax: `read [options] variable_name`. If you give `read` multiple variable names, it assigns input words to them in order; any remaining text goes into the last variable.
- `-p "prompt"`: Displays a prompt before waiting for input. The prompt does not add a newline.

```bash
read -r -p "Type a number: " number
echo "You entered: $number"
```

Common options:

- `-r`: Reads backslashes literally instead of treating them as escape characters. This is usually the option to use for ordinary text input.
- `-p "prompt"`: Prints a prompt before reading input.
- `-s`: Hides the characters as they are typed, useful for password input. Print a newline afterward with `printf '\n'` if needed.
- `-n number`: Stops after reading the specified number of characters instead of waiting for Enter.
- `-t seconds`: Stops waiting after the specified number of seconds. `read` returns a non-zero status if it times out.
- `-a array_name`: Splits the input into words and stores them as elements of an indexed array.

Examples:

```bash
read -r -p "Enter a path: " path
read -r -s -p "Enter a password: " password
printf '\n'
read -r -n 1 -p "Continue? (y/n) " answer
printf '\n'
read -r -t 5 -p "You have 5 seconds: " response
read -r -a items -p "Enter some words: "
```

Use `read -r` for normal text input unless you specifically need backslashes to be interpreted. For more details, check `help read` in Bash.

---

## Script arguments

- What it is: Script arguments are values that you pass to a script when you run it. In Bash, they are stored in special variables like `$1`, `$2`, and `$@`.
- Why it matters: Arguments let a script behave differently depending on what the user provides, without changing the script itself.
- Practical use: You can use arguments to pass a filename, a directory, a name, or a mode such as `start` or `stop`.
- Example layout:

```bash
#!/usr/bin/env bash

echo "Hello, $1!"
echo "You passed $# arguments."
```

If you run:

```bash
./greet.sh Alice
```

Then `$1` becomes `Alice`, and `$#` becomes `1`.

### $1, $2, $@, and $# etc

- Positional parameters: `$1` through `$9` refer to the first nine arguments passed to the script. For a parameter with two or more digits, wrap the number in braces: `${10}`, `${11}`, and so on. Without braces, `$10` means `$1` followed by the character `0`, not the tenth argument.
- Other useful parameters: `$@` expands to all arguments, and `$#` gives the number of arguments passed.
- `$0` contains the name or path used to run the script.
- `"$*"` combines all arguments into one word, separated by the first character of `IFS` (a space by default).
- `shift` removes the first positional parameter: `$2` becomes `$1`, `$3` becomes `$2`, and `$#` decreases by one.
- Why it matters: These variables let your script access the values the user passed in and react to them.
- Practical use: You can build scripts that work with any file name, user name, or folder path.
- Example:

```bash
#!/usr/bin/env bash

echo "First argument: $1"
echo "Second argument: $2"
echo "Ninth argument: $9"
echo "Tenth argument: ${10}"
printf 'All arguments: <%s>\n' "$@"
echo "Total arguments: $#"
```

Run it with ten arguments, for example `./script.sh one two three four five six seven eight nine ten`. In this example, `$9` is `nine` and `${10}` is `ten`. Quote `"$@"` when passing all arguments to another command; this preserves each argument as a separate value, including arguments that contain spaces.

---

## Quoting

- What it is: Quoting tells Bash how to treat text, especially when a value contains spaces, special characters, or variable expansions.
- Why it matters: Without quotes, Bash may split words unexpectedly or treat special characters as instructions instead of plain text.
- Practical use: Quoting is important when working with file names, folder paths, user input, and messages that contain spaces.
- Example layout:

```bash
#!/usr/bin/env bash

name="Alice Smith"
echo "$name"
echo '$name'
```

In Bash, double quotes allow variable expansion, while single quotes keep text literal.

### Double quotes

- What it is: Double quotes `"..."` allow variables inside the string to be expanded, while still keeping spaces together as one value.
- Why it matters: This is useful when you want to print a variable inside a sentence without breaking the value into multiple words.
- Practical use: You often use double quotes around values passed to commands or output messages.
- Example layout:

```bash
name="Alice"
echo "Hello, $name!"
```

### Single quotes

- What it is: Single quotes `'...'` prevent Bash from expanding variables or interpreting special characters inside the string.
- Why it matters: This keeps the text literal and is useful when you want to print text exactly as written.
- Practical use: Use single quotes for exact text, especially when you do not want variables to expand.
- Example layout:

```bash
name="Alice"
echo 'Hello, $name!'
```

### Why quoting matters

- What it is: Quoting helps preserve the exact value of a string instead of letting Bash split it into multiple pieces.
- Why it matters: This is especially important when a value contains spaces or special symbols.
- Practical use: Before quoting, a command like `mkdir my folder` would be treated as two arguments instead of one path. With quotes, `mkdir "my folder"` works correctly.
- Example layout:

```bash
mkdir "my folder"
```

---

## Exit status

- What it is: Every command in Bash ends with an exit status, which tells the shell whether the command succeeded or failed.
- Why it matters: Exit statuses help you write scripts that can react to success or failure, such as stopping early, retrying a command, or printing a helpful message.
- Practical use: You use exit status when you want a script to check if a command worked and decide what to do next.
- Example layout:

```bash
#!/usr/bin/env bash

ls /tmp
echo "Exit status: $?"
```

If `ls /tmp` succeeds, the exit status is `0`. If it fails, the exit status is a non-zero number, usually `1` or another error code.

### Success and failure

- What it is: In Bash, a command that works correctly usually returns exit status `0`.
- Why it matters: `0` means success, while any other value usually means something went wrong.
- Practical use: Scripts often check the exit status of a command before continuing.
- Example layout:

```bash
cp file.txt backup.txt
if [[ $? -eq 0 ]]; then
  echo "Copy succeeded"
else
  echo "Copy failed"
fi
```

### Checking the exit status

- What it is: `$?` is a special Bash variable that contains the exit status of the most recently executed command.
- Why it matters: It lets you inspect whether the previous command succeeded or failed.
- Practical use: This is useful for debugging scripts and making decisions based on command results.
- Example layout:

```bash
mkdir my_folder
echo "$?"
```

If the command works, the output may be `0`. If it fails, you will see a different number.

### Why exit status matters in scripts

- What it is: Exit status is the shell’s way of reporting “did this work?”
- Why it matters: Many Bash tools and script commands depend on this information to decide whether to continue or stop.
- Practical use: You can use it to prevent a script from continuing after a bad command or to show a custom error message.
- Example layout:

```bash
#!/usr/bin/env bash

mkdir backup
if [[ $? -ne 0 ]]; then
  echo "Failed to create backup folder"
  exit 1
fi

echo "Backup folder ready"
```

This example checks whether the folder creation worked. If it did not, the script prints an error and exits immediately.

---

## Basic control flow

- What it is: Control flow is the order in which a Bash script runs commands. It allows a script to make decisions and choose different paths based on conditions.
- Why it matters: Without control flow, a script would do the same thing every time. With it, your script can react to input, files, values, and results.
- Practical use: You use control flow to check if a file exists, whether a number is greater than another value, or whether a user entered a valid answer.
- Example layout:

```bash
#!/usr/bin/env bash

age=20

if [[ $age -ge 18 ]]; then
  echo "You are an adult."
fi
```

This script checks a condition and only runs the command if the condition is true.

### If statements

- What it is: An `if` statement checks a condition and runs the commands inside it only when the condition is true.
- Why it matters: This is one of the most important parts of scripting because it lets your program make decisions.
- Practical use: You can use `if` to check for a file, compare values, or test whether a user input is valid.
- Example layout:

```bash
#!/usr/bin/env bash

number=10

if [[ $number -gt 5 ]]; then
  echo "The number is greater than 5"
fi
```

The condition is `[[ $number -gt 5 ]]`. If that condition is true, Bash runs the code inside the `if` block.

### If-else statements

- What it is: An `if-else` statement gives your script two paths: one for when the condition is true and one for when it is false.
- Why it matters: This lets you handle both outcomes cleanly instead of only handling the successful case.
- Practical use: You might use it to show a message for valid input and a different message for invalid input.
- Example layout:

```bash
#!/usr/bin/env bash

score=75

if [[ $score -ge 70 ]]; then
  echo "Pass"
else
  echo "Fail"
fi
```

If the score is 70 or more, the script prints `Pass`. Otherwise, it prints `Fail`.

### If-elif-else

- What it is: An `elif` block lets you check multiple conditions in order.
- Why it matters: It is useful when you have more than two possible outcomes.
- Practical use: You can use it for grade ranges, menu choices, or user permission checks.
- Example layout:

```bash
#!/usr/bin/env bash

value=7

if [[ $value -gt 10 ]]; then
  echo "Large"
elif [[ $value -gt 5 ]]; then
  echo "Medium"
else
  echo "Small"
fi
```

This script checks several conditions in order and runs only the matching block.

---

## Basic loops

- What it is: A loop repeats a block of code multiple times instead of writing the same commands over and over.
- Why it matters: Loops are one of the most useful tools in Bash because they let you process many files, values, or tasks efficiently.
- Practical use: You use loops when you want to rename files, print numbers, check a list, or repeat a command until a condition changes.
- Example layout:

```bash
#!/usr/bin/env bash

for number in 1 2 3 4 5; do
  echo "$number"
done
```

This script runs the `echo` command five times, once for each value in the list.

### For loop

- What it is: A `for` loop repeats a block of code once for each item in a list.
- Why it matters: It is ideal when you know exactly what values you want to process.
- Practical use: You can loop through names, numbers, file names, or a list of folders.
- Example layout:

```bash
#!/usr/bin/env bash

for name in Alice Bob Charlie; do
  echo "Hello, $name!"
done
```

This prints a greeting for each person in the list.

### For loop with a range

- What it is: A `for` loop can also iterate over a numeric range.
- Why it matters: This is helpful when you want to repeat something a fixed number of times.
- Practical use: You can count, generate values, or perform a task a certain number of times.
- Example layout:

```bash
#!/usr/bin/env bash

for i in {1..5}; do
  echo "Iteration $i"
done
```

This prints five iterations, starting at 1 and ending at 5.

### While loop

- What it is: A `while` loop keeps running as long as a condition remains true.
- Why it matters: It is useful when you do not know ahead of time how many times the loop should run.
- Practical use: You can use it for counters, waiting for input, or repeating an action until a condition changes.
- Example layout:

```bash
#!/usr/bin/env bash

count=1

while [[ $count -le 5 ]]; do
  echo "Count: $count"
  ((count++))
done
```

This loop runs while the count is less than or equal to 5.

### Why loops matter

- What it is: Loops let a script automate repeated work without writing the same lines over and over.
- Why it matters: This makes scripts shorter, easier to read, and much more useful.
- Practical use: Beginners often use loops to process files, print lists, and automate repetitive tasks.
- Example layout:

```bash
#!/usr/bin/env bash

for file in *.txt; do
  echo "Processing $file"
done
```

This loops through every `.txt` file in the current directory and processes each one.

---

## Basic functions

- What it is: A function is a reusable block of code that you can call by name whenever you need it.
- Why it matters: Functions help you avoid repeating the same commands in multiple places and make scripts easier to organize.
- Practical use: You can use functions for greetings, file cleanup, setup steps, or any task you want to reuse.
- Example layout:

```bash
#!/usr/bin/env bash

say_hello() {
  echo "Hello!"
}

say_hello
```

This script defines a function named `say_hello` and then calls it.

### Defining a function

- What it is: A function is defined with a name followed by parentheses and a block of commands.
- Why it matters: Naming a block of code gives you a simple way to reuse it anywhere in the script.
- Practical use: You might define a function that creates a folder, prints a message, or checks if a file exists.
- Example layout:

```bash
#!/usr/bin/env bash

greet() {
  echo "Welcome, $1!"
}

greet Alice
```

This function accepts an argument and uses it inside the message.

### Calling a function

- What it is: Calling a function means running the code stored inside it by typing its name.
- Why it matters: This makes scripts easier to read and maintain because you can reuse a block of logic instead of copying it repeatedly.
- Practical use: You can call a function after defining it, or call it from inside another function.
- Example layout:

```bash
#!/usr/bin/env bash

print_date() {
  echo "Today is $(date)"
}

print_date
```

This function prints the current date when it is called.

### Function arguments

- What it is: Functions can accept arguments just like scripts do, using `$1`, `$2`, and so on.
- Why it matters: This makes functions flexible and useful for different inputs.
- Practical use: You can pass names, paths, numbers, or messages into a function.
- Example layout:

```bash
#!/usr/bin/env bash

welcome() {
  echo "Hello, $1!"
}

welcome "Alice"
welcome "Bob"
```

Each function call uses the next argument value.

### Why functions matter

- What it is: Functions let you group related commands into one reusable unit.
- Why it matters: This keeps scripts cleaner and easier to debug, especially as they grow larger.
- Practical use: Functions are helpful for creating reusable tools, repeating tasks, and separating logic into clear pieces.
- Example layout:

```bash
#!/usr/bin/env bash

create_folder() {
  mkdir -p "$1"
  echo "Folder created: $1"
}

create_folder projects
```

This function creates a folder and prints a message after it runs.

---

## Debugging basics

- What it is: Debugging is the process of checking why a script is not working the way you expect.
- Why it matters: Even small script mistakes can cause big confusion. Debugging helps you find the issue quickly and fix it safely.
- Practical use: You use debugging when a script has the wrong output, exits unexpectedly, or stops at the wrong step.
- Example layout:

```bash
#!/usr/bin/env bash

set -x

name="Alice"
echo "Hello, $name!"
```

The `set -x` command prints each command as Bash runs it, which helps you track what is happening.

### Using `set -x`

- What it is: `set -x` enables shell tracing, which prints each command before it runs.
- Why it matters: This is one of the easiest ways to see what your script is actually doing.
- Practical use: You use it when you want to understand the order of commands and check the exact values being used.
- Example layout:

```bash
#!/usr/bin/env bash

set -x

count=1
((count += 2))
echo "Count is $count"
```

This makes the script print each step, making it easier to follow.

### Printing values with `echo`

- What it is: `echo` is one of the simplest debugging tools because it lets you print variable values and messages at different stages.
- Why it matters: If a variable is wrong or empty, printing it helps you find the problem quickly.
- Practical use: You can check values before and after a command to confirm the script is doing the right thing.
- Example layout:

```bash
#!/usr/bin/env bash

name="Alice"
echo "Before: $name"
name="Bob"
echo "After: $name"
```

This shows the value of the variable before and after it changes.

### Checking exit status

- What it is: When a command fails, checking its exit status helps identify the problem.
- Why it matters: A script may appear to run but still fail because a command returned an error.
- Practical use: You can compare the result of a command with `0` to confirm success or fail gracefully.
- Example layout:

```bash
#!/usr/bin/env bash

ls /missing_directory
if [[ $? -ne 0 ]]; then
  echo "The directory does not exist"
fi
```

This checks whether the previous command failed and prints a useful message.

### Using `bash -x`

- What it is: `bash -x script.sh` runs a script in trace mode without editing the script itself.
- Why it matters: This is helpful when you want to debug a script without permanently changing it.
- Practical use: You can use it to inspect each action as the script runs.
- Example layout:

```bash
bash -x script.sh
```

This prints each command and its values while the script is running.

### Common debugging habits

- What it is: Good debugging habits include checking one thing at a time, printing variables, and testing small sections of code.
- Why it matters: Small, focused checks are easier to understand than reading a long complicated script all at once.
- Practical use: When a script fails, start by checking the variables, conditions, and results of the most recent command.
- Example layout:

```bash
#!/usr/bin/env bash

name="Alice"

echo "Debug: name=$name"

if [[ -z "$name" ]]; then
  echo "Name is empty"
fi
```

This helps confirm whether the value is present before the script continues.

### Why debugging is important

- What it is: Debugging is how you learn what your script is actually doing behind the scenes.
- Why it matters: Every beginner runs into broken scripts. Debugging is a normal and important skill in Bash and programming.
- Practical use: As your scripts grow bigger, debugging becomes more important because small errors can affect many lines.
- Example layout:

```bash
#!/usr/bin/env bash

set -x

echo "Starting script"
mkdir -p test_folder
```

This example makes it easier to see whether the script reaches each step and whether the commands succeed.

---