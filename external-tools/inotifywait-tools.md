# inotify-tools package

- A set of command line programs that interface with the Linux kernel's `inotify` subsystem.
- Used to monitor filesystem events (file creation, modification, deletion) in real-time without needing timer loops.

**note**: this is not a built in this needs to be externially installed

## Contents
- [`Commands`](#commands)
- [`Installing the Package`](#installing-the-package)
- [`What Tools Are Inside?`](#what-tools-are-inside)
  - [`inotifywait`](#inotifywait)
  - [`inotifywatch`](#inotifywatch)
  - [`fsnotifywait & fsnotifywatch`](#fsnotifywait--fsnotifywatch)
  - [`libinotifytools`](#libinotifytools)


### Common Flags & Options
- **-m**, **--monitor**: Keeps the program running indefinitely to listen for continuous events instead of exiting after the first one.
- **-r**, **--recursive**: Watches a directory and all of its subdirectories recursively.
- **-e**, **--event**: Limits listening to specific filesystem events only (e.g., `create`, `modify`, `delete`).
- **-q**, **--quiet**: Suppresses output, printing only essential information.
- **--format**: Formats the output using specific tokens (like `%f` for filename or `%w` for directory path).
- **--timefmt**: Sets the time format string used alongside format tokens.

## Installing the Package

> can change depending on your distro.

**arch**:
```bash
sudo pacman -S inotify-tools
```

**debian / ubuntu**:
```bash
sudo apt install inotify-tools
```

**fedora**:
```bash
sudo dnf install inotify-tools
```

## What Tools Are Inside?

- The `inotify-tools` package comes with a few command line programs designed to work with the kernel.



### inotifywait
- **inotifywait** is a command line tool designed to wait for changes to files and directories. Instead of polling in a continuous loop, it listens to the kernel and blocks until a specific filesystem event occurs.

To watch a directory continuously and print all events:
```bash
inotifywait -m /path/to/folder
```

Example in a script:
```bash
inotifywait -m -e create --format '%f' /path/to/folder | while read FILENAME; do
    echo "New file detected: $FILENAME"
done
```



### inotifywatch
- **inotifywatch** is a command line tool designed to gather filesystem usage statistics. Instead of streaming events in real time, it listens to the kernel and outputs a summary table showing how often files or directories were accessed, modified, or created.

To get statistics on a directory for a set amount of time (e.g., 30 seconds):
```bash
inotifywatch -v -t 30 /path/to/folder
```

Example collecting recursively:
```bash
inotifywatch -v -r /path/to/folder
```



### fsnotifywait & fsnotifywatch
- **fsnotifywait** and **fsnotifywatch** are alternative tools that interface with Linux's newer `fanotify` subsystem by default, while keeping `inotify` as a fallback. They offer similar syntax to `inotifywait` and `inotifywatch`, but leverage `fanotify` for broader capabilities.

To use fsnotifywait for monitoring:
```bash
fsnotifywait -m /path/to/folder
```

Example in a script:
```bash
fsnotifywait -m -e create --format '%f' /path/to/folder | while read FILENAME; do
    echo "New file detected via fanotify: $FILENAME"
done
```