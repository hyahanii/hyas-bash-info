# 1.0 - Terminal Utilities

## Contents

- [`man`](#man)
- [`history`](#history)
- [`clear`](#clear)
- [`which`](#which)
- [`command -v`](#command--v)

## Terminal utilities

### man
- What it stands for: Manual
- What it does: Opens the built-in manual pages for a command, showing its purpose, options, and examples.
- Why use it: When you forget how a command works or what flags it supports, `man` is the fastest place to look.

- How to use it:
```bash
man ls
```

- *man [command]* (Open Manual Page): Shows the manual page for a specific command.
Example:
```bash
man grep
```

- *q* (Quit Manual): Press `q` inside the manual viewer to exit back to the terminal.
Example:
```bash
man ls
# press q to quit
```

- *man -k [keyword]* (Search Manual Entries): Searches for commands related to a keyword.
Example:
```bash
man -k network
```

Note: If you are unsure what a command does, `man` is usually the first place to check before guessing.


### history
- What it does: Displays commands you have entered in the current Bash session, along with a number for each command.
- Why use it: Useful when you want to find a command you used earlier so you can review or run it again.

- How to use it:
```bash
history
# Output:
#   1  pwd
#   2  ls
#   3  cd Documents
```

- *history [number]* (Show Recent Commands): Shows only the most recent number of commands.
Example:
```bash
history 5
```

- *!!* (Repeat Previous Command): Runs the last command again. Check it first if it could change or delete files.
Example:
```bash
!!
```

Note: Bash may save command history between sessions, depending on its configuration.


### clear
- What it does: Clears the visible text from the terminal window, leaving you with a fresh screen.
- Why use it: Useful when the terminal has become cluttered and you want to make new output easier to read.
- How to use it:
```bash
clear
```

- *Ctrl + L* (Keyboard Shortcut): Clears the visible terminal screen without typing the command.

Note: `clear` only clears what is visible; it does not delete command history or files.


### which
- What it does: Shows the file path of an executable command found in your `PATH`.
- Why use it: Useful for checking which program will run when you enter a command, or where that program is installed.

- How to use it:
```bash
which ls
# Output: /usr/bin/ls
```

- *which [command]* (Find a Command): Replace `[command]` with the command whose executable location you want to find.
Example:
```bash
which bash
```

Note: `which` may not find shell built-ins such as `cd`. Use `command -v` to check for those as well.


### command -v
- What it does: Tells you how Bash will interpret a command name. It can identify executable paths, shell built-ins, aliases, and functions.
- Why use it: Useful for checking whether a command is available and finding out what kind of command it is. Unlike `which`, it is a Bash built-in and can check commands such as `cd`.

- How to use it:
```bash
command -v ls
# Output: /usr/bin/ls
```

- *command -v [name]* (Check a Command): Replace `[name]` with the command you want to check.
Example:
```bash
command -v cd
# Output: cd
```

Note: If the command is not found, `command -v` prints nothing and returns a non-zero status.