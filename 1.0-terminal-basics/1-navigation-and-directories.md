# 1.0 - Navigation and Directories

## Contents

- [`pwd`](#pwd)
- [`ls`](#ls)
- [`ls -la`](#detailed-listing)
- [`cd`](#change-directory)
- [`cd ..`](#parent-directory)
- [`cd ~`](#home-directory)

## Navigation commands


### pwd
- What it stands for: Print Working Directory
- What it does: Prints the exact absolute file path of the directory you are currently in (e.g., /home/user/documents).
- Why use it: When navigating in the terminal, it is easy to get lost. pwd tells you your exact current location in the filesystem.

- How to use it: 
```bash
pwd
# Output: /home/username
```


### ls
- What it stands for: List
- What it does: Displays the names of files and folders contained within your current working directory.
- Why use it: It lets you see what files and directories are available to interact with in your current location.

- How to use it: 
```bash
ls
# Output: Documents Downloads file.txt
```


# Detailed listing

### ls -la
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


# Change directory

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


# Parent directory

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


# Home directory

### cd ~: Go To Home Directory
- What it stands for: Change Directory to Tilde (Home)
- What it does: Instantly takes you to the user home directory (e.g., /home/username).
- Why use it: The tilde symbol *~* is a built-in shortcut for your home directory. It provides a fast way to return home from anywhere in the filesystem.

Note: Typing just *cd* without any arguments does the same exact thing.