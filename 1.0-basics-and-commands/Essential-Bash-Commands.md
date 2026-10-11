# Essential Bash Commands

## 1. File And Directory Navigation
- [`pwd`](#pwd-print-working-directory)       # Print working directory (shows where you are)
- ls        # List files and folders in the current directory
- ls -la    # List all files (including hidden ones) with detailed info
- cd [dir]  # Change directory (e.g., cd /var/log)
- cd ..     # Move up one directory level
- cd ~      # Navigate straight to your user home directory


## 1.5. File And Directory Navigation Definitions

*pwd*: Print Working Directory
- What it stands for: Print Working Directory
- What it does: Prints the exact absolute file path of the directory you are currently in (e.g., /home/user/documents).
- Why use it: When navigating in the terminal, it is easy to get lost. pwd tells you your exact current location in the filesystem.

- How to use it: 
```bash
pwd
# Output: /home/username
```

*ls*: List
- What it stands for: List
- What it does: Displays the names of files and folders contained within your current working directory.
- Why use it: It lets you see what files and directories are available to interact with in your current location.
- How to use it: 
```bash
ls
# Output: Documents Downloads file.txt
```

*ls -la*: List All (Detailed)
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

*cd [dir]*: Change Directory
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

*cd ~*: Go To Home Directory
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