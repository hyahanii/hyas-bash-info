# 3.0 - Introduction to Programming in Bash

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
- [`Your first Bash script`](#your-first-bash-script)
- [`Basic control flow`](#basic-control-flow)
  - [`If statements`](#if-statements)
  - [`If-else statements`](#if-else-statements)
- [`Basic loops`](#basic-loops)
  - [`For loop`](#for-loop)
  - [`While loop`](#while-loop)
- [`Basic functions`](#basic-functions)
- [`Debugging basics`](#debugging-basics)

This chapter introduces the basic building blocks of Bash programming. It is meant to be a gentle beginner-friendly starting point for writing simple scripts.

## What a Bash script is
- What is a bash script?: A Bash script is a plain text file that contains a series of Bash commands. When you run the script, the shell reads the file line by line and executes each command in order.
- Why it matters: Scripts help automate repetitive tasks, save time, and let you build simple tools without manually typing the same commands over and over.
- Practical use: You can use Bash scripts for things like creating folders, moving files, checking system status, backing up data, or automating setup steps.
- Example layout:
```bash
#!/usr/bin/env bash

echo "Hello, world!"
ls -l
mkdir -p backup
```

A script usually has a .sh extension, but the file itself is just a normal text file containing commands.

## How Bash scripts work
- How do bash scripts work?: A Bash script is just a text file containing commands. When you run it, Bash opens the file and reads it from top to bottom. Each line is treated as a command, and the shell executes those commands in order unless something changes the flow, like a conditional, loop, or function call.
- Why it matters: Understanding the flow of a script helps you predict what will happen when it runs. It also makes debugging much easier when a script does something unexpected.
- Practical use: You use this idea every time you create a script to automate repeated tasks, such as creating files, checking folders, or renaming many items at once.
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
- Note: The name "hashbang/shebang" comes from the two characters `#` and `!` at the start of the line. In Unix-like systems, the kernel or shell sees `#!` and knows to pass the rest of the line to the interpreter. That is why the line is usually written as `#!/usr/bin/env bash`.
- Example layout:
```bash
#!/usr/bin/env bash
echo "Hello from Bash!"
```

### Making a script executable
- What it does: Making a script executable means giving it permission to run as a program.
- Why it matters: If a script is not executable, you can still run it with `bash script.sh`, but you cannot run it directly with `./script.sh`.
- Practical use: This is useful when you want to share scripts or run them like commands from the terminal.
- Note: `chmod` is short for “change mode,” and it changes the file permissions. The `+x` part means “add execute permission,” which allows the file to be run as a program. The `./` before a filename means “run this file from the current directory.” So `./script.sh` tells the shell: “execute the script located in the directory I’m currently in.”
- Example layout:
```bash
chmod +x script.sh
./script.sh
```

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


### Basic assignment


### Reading variables


---

## User input (read)


### read


---

## Script arguments


---

## Quoting


---

## Exit status


---

## Your first Bash script


---

## Basic control flow


### If statements


### If-else statements


---

## Basic loops


### For loop


### While loop


---

## Basic functions


---

## Debugging basics

---

## Summary
