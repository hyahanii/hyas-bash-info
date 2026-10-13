# Terminal Shortcuts and Controls

## Contents

- [Key notation](#key-notation)
- [Controlling running commands](#controlling-running-commands)
- [Editing the command line](#editing-the-command-line)
- [Moving through command history](#moving-through-command-history)
- [Completion and the terminal display](#completion-and-the-terminal-display)
- [Notes](#notes)

This document lists useful keyboard shortcuts for working in a terminal. Some shortcuts are handled by Bash's line editor, while others are handled by the terminal program. Their behavior can vary between systems and terminal settings.

## Key notation

- `Ctrl` means hold Control while pressing the listed key.
- `Alt` means hold Alt while pressing the listed key. On some terminals, `Esc` followed by the key works instead.

## Controlling running commands

- `Ctrl+C` — interrupt the foreground command
- `Ctrl+Z` — suspend the foreground command
- `Ctrl+D` — send end-of-input (EOF)

## Editing the command line

- `Ctrl+A` — move to the start of the command line
- `Ctrl+E` — move to the end of the command line
- `Ctrl+U` — delete from the cursor to the start of the line
- `Ctrl+K` — delete from the cursor to the end of the line
- `Ctrl+W` — delete the word before the cursor
- `Ctrl+Y` — restore the most recently deleted text
- `Alt+B` — move back one word
- `Alt+F` — move forward one word

## Moving through command history

- `Up Arrow` / `Down Arrow` — move through previous commands
- `Ctrl+R` — search command history
- `Ctrl+G` — cancel a history search

## Completion and the terminal display

- `Tab` — complete a command, filename, or path when possible
- `Tab` twice — show possible completions when there is more than one match
- `Ctrl+L` — clear the visible terminal screen

## Notes

- `Ctrl+C` sends an interrupt signal; a program may handle it instead of exiting.
- `Ctrl+Z` suspends a job rather than terminating it. Use shell job-control commands such as `fg`, `bg`, or `kill` to manage it afterward.
- `Ctrl+D` sends EOF. At an empty Bash prompt, it usually exits that shell; while a command is reading input, it signals that no more input is available.
- Shortcut behavior can depend on the shell, terminal program, operating system, and key settings.