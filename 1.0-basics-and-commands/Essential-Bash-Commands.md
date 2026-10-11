# Essential Bash Commands

## Contents
- [`1. File And Directory Navigation`](#1-file-and-directory-navigation)
  - [`pwd`](#pwd-print-working-directory)
  - [`ls`](#ls-list)
  - [`ls -la`](#ls--la-list-all-detailed)
  - [`cd [dir]`](#cd-dir-change-directory)
  - [`cd ..`](#cd--move-up-one-level)
  - [`cd ~`](#cd--go-to-home-directory)
- [`2. File And Directory Manipulation`](#2-file-and-directory-manipulation)
  - [`mkdir [dir]`](#mkdir-dir-make-directory)
  - [`touch [file]`](#touch-file-touch-create-empty-file)
  - [`cp [source] [dest]`](#cp-source-dest-copy-file-or-directory)
  - [`mv [source] [dest]`](#mv-source-dest-move-or-rename-file-or-directory)
  - [`rm [file]`](#rm-file-remove-file)
- [`3. Viewing/Reading Files`](#3-viewingreading-files)
  - [`cat [file]`](#cat-file-concatenate-and-display)
  - [`less [file]`](#less-file-interactive-file-viewer)
  - [`head [file]`](#head-file-display-beginning-of-file)
  - [`tail [file]`](#tail-file-display-end-of-file)

## 1. File And Directory Navigation
- [`pwd`](#pwd-print-working-directory)         # Print working directory (shows where you are)
- [`ls`](#ls-list)          # List files and folders in the current directory
- [`ls -la`](#ls--la-list-all-detailed)      # List all files (including hidden ones) with detailed info
- [`cd [dir]`](#cd-dir-change-directory)    # Change directory (e.g., cd /var/log)
- [`cd ..`](#cd--move-up-one-level)     # Move up one directory level
- [`cd ~`](#cd--go-to-home-directory)      # Navigate straight to your user home directory


## 1.5. File And Directory Navigation Definitions

### pwd: Print Working Directory
- What it stands for: Print Working Directory
- What it does: Prints the exact absolute file path of the directory you are currently in (e.g., /home/user/documents).
- Why use it: When navigating in the terminal, it is easy to get lost. pwd tells you your exact current location in the filesystem.

- How to use it: 
```bash
pwd
# Output: /home/username
```

### ls: List
- What it stands for: List
- What it does: Displays the names of files and folders contained within your current working directory.
- Why use it: It lets you see what files and directories are available to interact with in your current location.
- How to use it: 
```bash
ls
# Output: Documents Downloads file.txt
```

### ls -la: List All (Detailed)
- What it stands for: List (with -l for Long format and -a for All files)
- What it does: Lists every file and folder—including hidden files (those starting with a dot like .bashrc), along with detailed metadata such as permissions, ownership, file size, and last modified date.
- Why use it: Use this when you need to view hidden configuration files or check file permissions and sizes.
- How to use it: 
```bash
ls -la
# Output: 
# drwxr-xr-x  5 user user 4096 Jan 1 12:00 .
# drwxr-xr-x 20 user user 4096 Jan 1 12:00 ..
# -rw-r--r--  1 user user  220 Jan 1 12:00 .bashrc
# drwxr-xr-x  2 user user 4096 Jan 1 12:00 Documents
```

Note: 
- You can also use *ls -l* on its own for just the long format details without hidden files.
- Or you can use *ls -a* to see hidden files without the long format table.

### cd [dir]: Change Directory
- What it stands for: Change Directory
- What it does: Switches your current working directory to the target directory specified in [dir].
- Why use it: Used to navigate into different folders within the filesystem.
- Examples on how to use it:
```bash
ls
# Example Output: Desktop  Documents  Downloads  konsole  Music
cd Documents
pwd
# Output: /home/username/Documents
```

### cd ..: Move Up One Level
- What it stands for: Change Directory to Parent
- What it does: Moves you up exactly one directory level in the system folder hierarchy.
- Why use it: The ".." symbol represents the parent directory. It allows you to step backward out of your current folder without typing out a full path.
- How to use it: 
```bash
pwd
# Output: /home/username/Documents
cd ..
pwd
# Output: /home/username
```

### cd ~: Go To Home Directory
- What it Stands for: Change Directory to Tilde (Home)
- What it does: Instantly takes you to the user home directory (e.g., /home/username).
- Why use it: The tilde symbol *~* is a built-in shortcut for your home directory. It provides a fast way to return home from anywhere in the filesystem. 

Note: Typing just *cd* without any argumentsdoes the same exact thing.

- How to use it: 
```bash
cd ~
pwd
# Output: /home/username
```

## 2. File And Directory Manipulation
- [`mkdir [dir]`](#mkdir-dir-make-directory)        # Make directory (create a new folder)
- [`touch [file]`](#touch-file-touch-create-empty-file)      # Create a new, empty file (or update file timestamps)
- [`cp [source] [dest]`](#cp-source-dest-copy-file-or-directory) # Copy files or directories
- [`mv [source] [dest]`](#mv-source-dest-move-or-rename-file-or-directory) # Move or rename files and directories
- [`rm [file]`](#rm-file-remove-file)          # Remove (delete) files

## 2.5. File And Directory Manipulation Definitions

### mkdir [dir]: Make Directory
- What it stands for: Make Directory
- What it does: Creates a new, empty directory (folder) with the specified name in your current working directory.
- Why use it: Used when you need to organize your files by creating new folders.
- How to use it: 
```bash
mkdir projects
ls
# Output: Documents Downloads projects
```

- *mkdir -p* (Make Parent Directories): Creates nested directories all at once if they dont already exist.
Example:
```bash
mkdir -p projects/bash/scripts
```

### touch [file]: Touch (Create Empty File)
- What it stands for: Touch
- What it does: Creates a new, empty file with the specified name, or updates the timestamp of an existing file.
- Why use it: The fastest way to create a blank file (like a script or text file) without opening a full text editor.
- How to use it: 
```bash
touch script.sh
ls
# Output: projects script.sh
touch words.txt
# Output: projects script.sh words.txt
```

### cp [source] [dest]: Copy File or Directory
- What it stands for: Copy
- What it does: Copies a file or directory from a source location to a destination location, creating an exact duplicate.
- Why use it: Used when you want to duplicate a file or folder (e.g., making a backup copy before editing it).
- How to use it: 
```bash
cp script.sh backup.sh
ls
# Output: projects script.sh words.txt backup.sh
```

- *cp -r* (Recursive Copy): Required when copying an entire directory instead of just a single file.
Example:
```bash
cp -r projects/ backup_projects/
```

### mv [source] [dest]: Move or Rename File or Directory
- What it stands for: Move
- What it does: Moves a file or directory from one location to another, or renames it if the destination name is different within the same location.
- Why use it: Used to reorganize files into different directories or give them a new name.
- How to use it: 
```bash
mv script.sh new_script.sh
ls
# Output: projects words.txt backup.sh new_script.sh
```

- *mv -i* (Interactive Move/Rename): Prompts you for confirmation before overwriting an existing file, preventing accidental data loss.
Example:
```bash
mv -i script.sh backup.sh
# Output: overwrite 'backup.sh'? (y/n)
```

### rm [file]: Remove File
- What it stands for: Remove
- What it does: Permanently deletes the specified file from the filesystem. 
- (Note: Unlike a graphical desktop, the terminal does not have a recycle bin or trash folder files deleted with `rm` are gone instantly).
- Why use it: Used to clean up old, temporary, or unneeded files.
- How to use it: 
```bash
ls
# Output: projects backup.sh new_script.sh words.txt
rm words.txt
ls
# Output: projects backup.sh new_script.sh
```

- *rm -i* (Interactive Remove): Prompts you before deleting a file so you don't delete something by accident.
Example:
```bash
rm -i file.txt
# Output: remove 'file.txt'? (y/n)
```

- *rm -r* (Recursive Remove): Required to delete a directory and all of its contents. (Use with extreme caution)
Example:
```bash
rm -r old_folder/
```

- *rm -ri* (Interactive Recursive Remove): Combines both flags. It deletes a directory and its contents recursively, but prompts you for confirmation before deleting every single file. This is the safest way to delete a folder full of files without risking accidental deletion.
Example:
```bash
rm -ri old_folder/
# Output: 
# descend into directory 'old_folder/'? y
# remove 'old_folder/file1.txt'? y
# remove 'old_folder/file2.txt'? n
```

## 3. Viewing/Reading Files
- [`cat [file]`](#cat-file-concatenate-and-display)
- [`less [file]`](#less-file-interactive-file-viewer)
- [`head [file]`](#head-file-display-beginning-of-file)
- [`tail [file]`](#tail-file-display-end-of-file)

## 3.5. Viewing/Reading Files Definitions

### cat [file]: Concatenate and Display
- What it stands for: Concatenate
- What it does: Reads a file and prints its entire content directly into the terminal window.
- Why use it: The quickest way to view short text files without leaving yur command line prompt.
- How to use it:
```bash
cat words.txt
# Output: 
# apple
# banana
# cherry
```

- *cat -n* (Numbered Lines): Displays the line numbers alongside the content. Example:
```bash
cat -n words.txt
# Output:
#      1  apple
#      2  banana
#      3  cherry
```


### less [file]: Interactive File Viewer
- What it stands for: Interactive File Viewer
- What it does: Opens a file in a scrollable, full screen reader view that lets you navigate forward and backward through large text files.
- Why use it: Prevents large files from flooding your terminal output. It loads fast because it doesn't load the entire file into memory at once.
- How to use it:
```bash
less large_log.txt
```

- Navigation shortcuts inside *less*:
  - *Up / Down Arrows* or *j / k*: scroll line by line
  - *Spacebar* or *Page Down*: Scroll forward one full page.
  - *b*: Scroll backward one full page.
  - /search_term: Searches forward for a specific word.
  - *q*: Quit *less* and return to your terminal.

### head [file]: Display Beginning of File
- What it stands for: Head
- What it does: Outputs the first few lines of a file (10 lines by default).
- Why use it: Useful for quickly inspecting the structure or headers of a large dataset or config file.
- How to use it:
```bash
head server.log
# Output: Prints the first 10 lines of server.log
```

- *head -n [Number]* (Custom Line Count): Specifies exactly how many lines from the top you want to view.
Example:
```bash
head -n 50 server.log
# Output: Prints the first 50 lines of server.log
```

### tail [file]: Display End of File
- What it stands for: Tail
- What it does: Outputs the last few lines of a file (10 lines by default).
- Why use it: Useful for checking the most recent entries at the end of a log or output file. 
- How to use it:
```bash
tail server.log
# Output: Prints the last 10 lines of server.log
```

- *tail -n [Number]* (Custom Line Count): Specifies exactly how many lines from the bottom you want to view.
Example:
```bash
tail -n 20 server.log
# Output: Prints the last 20 lines of server.log
```

## 4. Searching And Filtering Files
- [`grep [pattern] [file]`](#grep-pattern-file-global-regular-expression-print)        # Search for a specific pattern of text within files
- [`find [dir] [criteria]`](#find-dir-criteria-find-files-and-directories)      # Search for files and directories across the filesystem
- [`wc [file]`](#wc-file-word-count)                       # Count lines, words, and characters in a file
- [`sort [file]`](#sort-file-sort-lines-of-text-files)                    # Sort lines of text files
- [`uniq [file]`](#uniq-file-report-or-omit-repeated-lines)                # Report or omit repeated lines in a file
- [`cut [file]`](#cut-file-remove-sections-from-each-line-of-files)                     # Remove or extract sections from each line of a file

## 4.5. Searching And Filtering Files Definitions

### grep [pattern] [file]: Global Regular Expression Print
- What it stands for: Global Regular Expression Print
- What it does: Searches for a specific pattern of text within a file and prints every line that contains a match.
- Why use it: Its the fastest way to scan through large text files, configuration sheets, or logs to find specific words, terms, or error messages.
- How to use it:
```bash
grep "apple" words.txt
# Output: 
# apple
```

- *grep -i* (Case-Insensitive Search): Ignores capitalization so it finds the search term whether it is lowercase, upperacase, or mixed
Example:
```bash
grep -i "apple" words.txt
# Output:
# Apple
# apple
# APPLE
```

### find [dir] [criteria]: Find Files and Directories
- What it stands for: 
- What it does: 
- Why use it: 
- How to use it:
```bash

```

### wc [file]: Word Count
- What it stands for: 
- What it does: 
- Why use it: 
- How to use it:
```bash

```

### sort [file]: Sort Lines of Text Files
- What it stands for: 
- What it does: 
- Why use it: 
- How to use it:
```bash

```

### uniq [file]: Report or Omit Repeated Lines
- What it stands for: 
- What it does: 
- Why use it: 
- How to use it:
```bash

```

### cut [file]: Remove Sections from Each Line of Files
- What it stands for: 
- What it does: 
- Why use it: 
- How to use it:
```bash

```