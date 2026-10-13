# 1.0 - File Management

## Contents

- [`mkdir`](#mkdir)
- [`touch`](#touch)
- [`cp`](#cp)
- [`mv`](#mv)
- [`rm`](#rm)

## File and directory commands

### mkdir [dir]: Make Directory
- What it stands for: Make Directory
- What it does: Creates a new, empty directory (folder) with the specified name in your current working directory.
- Why use it: Used when you need to organize your files by creating new folders.

- How to use it: 
```bash
ls
# Output: Documents Downloads
mkdir projects
ls
# Output: Documents Downloads projects
```

- *mkdir -p* (Make Parent Directories): Creates nested directories all at once if they don't already exist.
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
ls
# Output: projects
touch script.sh
ls
# Output: projects script.sh
touch words.txt
ls
# Output: projects script.sh words.txt
```


### cp [source] [dest]: Copy File or Directory
- What it stands for: Copy
- What it does: Copies a file or directory from a source location to a destination location, creating an exact duplicate.
- Why use it: Used when you want to duplicate a file or folder (e.g., making a backup copy before editing it).

- How to use it: 
```bash
ls
# Output: projects script.sh words.txt 
cp script.sh backup.sh
ls
# Output: projects script.sh words.txt backup.sh
```

- *cp -r* (Recursive Copy): Required when copying an entire directory instead of just a single file.
Example:
```bash
cp -r projects/ backup_projects/
```

Note: If the destination is an existing file, `cp` overwrites it without asking. Use `cp -i` to be prompted before overwriting. If the destination is an existing directory, the copied file is placed inside it.


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
ls
# Output: projects backup.sh new_script.sh words.txt
mv -i script.sh backup.sh
# Output: overwrite 'backup.sh'? (y/n)
```


### rm [file]: Remove File
- What it stands for: Remove
- What it does: Permanently deletes the specified file from the filesystem. 
- (Note: Unlike a graphical desktop, the terminal does not have a recycle bin or trash folder; files deleted with `rm` are gone instantly.)
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