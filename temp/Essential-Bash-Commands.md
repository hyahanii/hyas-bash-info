
## 3. Viewing/Reading Files

- [`cat [file]`](#cat-file-concatenate-and-display)
- [`less [file]`](#less-file-interactive-file-viewer)
- [`head [file]`](#head-file-display-beginning-of-file)
- [`tail [file]`](#tail-file-display-end-of-file)

---

## 3.5. Viewing/Reading Files Definitions

### cat [file]: Concatenate and Display
- What it stands for: Concatenate
- What it does: Reads a file and prints its entire content directly into the terminal window.
- Why use it: The quickest way to view short text files without leaving your command line prompt.
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

## 4. Searching and Filtering Files

- [`grep [pattern] [file]`](#grep-pattern-file-global-regular-expression-print) # Search for a pattern within files
- [`find [dir] [criteria]`](#find-dir-criteria-find-files-and-directories) # Search for files and directories across the filesystem
- [`wc [file]`](#wc-file-word-count) # Count lines, words, and characters in a file
- [`sort [file]`](#sort-file-sort-lines-of-text-files) # Sort lines of text files
- [`uniq [file]`](#uniq-file-report-or-omit-repeated-lines) # Report or omit repeated lines in a file
- [`cut [file]`](#cut-file-remove-sections-from-each-line-of-files) # Remove or extract sections from each line of a file

---

## 4.5. Searching and Filtering Files Definitions

### grep [pattern] [file]: Global Regular Expression Print
- What it stands for: Global Regular Expression Print
- What it does: Searches for a specific pattern of text within a file and prints every line that contains a match.
- Why use it: It's the fastest way to scan through large text files, configuration sheets, or logs to find specific words, terms, or error messages.
- How to use it:
```bash
grep "apple" words.txt
# Output: 
# apple
```

- *grep -i* (Case-Insensitive Search): Ignores capitalization so it finds the search term whether it is lowercase, uppercase, or mixed.
Example:
```bash
grep -i "apple" words.txt
# Output:
# Apple
# apple
# APPLE
```

### find [dir] [criteria]: Find Files and Directories
- What it stands for: Find
- What it does: Searches through a directory tree and lists files or folders that match the given criteria. It can look for names, file types, sizes, dates, and more.
- Why use it: Useful when you know a file exists but not where it is. This is common for locating config files, project folders, logs, or large files in a messy directory structure.
- How to use it:
```bash
find . -name "*.txt"
# Output:
# ./notes.txt
# ./docs/ideas.txt
```

- *find [dir] -name "pattern"* (Name Search): Searches for files or directories whose names match a pattern
Example:
```bash
find /home/user -name "*.log"
# Output: /home/user/app.log /home/user/server/server.log
```

- *find [dir] -type d* (Directories Only): Limits the search to directories instead of files.
Example:
```bash
find . -type d
# Output:
# .
# ./docs
# ./projects
```

- *find [dir] -size +100M* (Size Search): Finds files larger than a specified size. 
Example:
```bash
find /home/user -size +100M
```

- *find [dir] -iname "pattern"* (Case Insensitive Name Search): Same as *-name*, but ignores uppercase/lowercase differences.
Example:
```bash
find . -iname "*.TXT"
```

Note: *.* means "current directory", so *find .* searches from wherever you are right now.


### wc [file]: Word Count
- What it stands for: Word Count
- What it does: Counts the number of lines, words, and characters in a file. By default, it prints all three values for the file you pass in.
- Why use it: Useful for checking file length, estimating how big a document is, or confirming that output was generated correctly.
- How to use it:
```bash
wc notes.txt
# Output:
# 12  45  260 notes.txt
```

- *wc -l* (Lines Only): Counts only the number of lines in a file.
Example:
```bash
wc -l notes.txt
# Output:
# 12 notes.txt
```

- *wc -w* (Words Only): Counts only the number of words.
Example:
```bash
wc -w notes.txt
# Output:
# 45 notes.txt
```

- *wc -c* (Characters Only): Counts the number of characters, including spaces and punctuation.
Example:
```bash
wc -c notes.txt
# Output:
# 260 notes.txt
```

Note: The output format is usually: lines words characters filename. So in the example above, the file has 12 lines, 45 words, and 260 characters.

### sort [file]: Sort Lines of Text Files
- What it stands for: Sort
- What it does: Reads a text file and sorts its lines in alphabetical order by default. It can also sort in reverse order or based on specific fields.
- Why use it: Useful when you need to organize names, log entries, or text lists so they are easier to read and compare.
- How to use it:
```bash
sort names.txt
# Output:
# alice
# bob
# charlie
```

- *sort -r* (Reverse Sort): Sorts the lines in reverse alphabetical order.
Example:
```bash
sort -r names.txt
# Output:
# charlie
# bob
# alice
```

- *sort -n* (Numeric Sort): Sorts lines as numbers instead of strings.
Example:
```bash
printf "10\n2\n7\n" | sort -n
# Output:
# 2
# 7
# 10
```

- *sort -u* (Unique Sort): Removes duplicate lines after sorting.
Example:
```bash
sort -u names.txt
```

Note: `sort` works best on plain text files. If you want to sort a file permanently, redirect the output into a new file using `>`. Example:
```bash
sort names.txt > sorted_names.txt
```

### uniq [file]: Report or Omit Repeated Lines
- What it stands for: Unique
- What it does: Filters out repeated adjacent lines in a file. It is commonly used after `sort`, because `uniq` only removes duplicates that are next to each other.
- Why use it: Useful when you want to clean up repeated entries in a list or log file without manually editing it.
- How to use it:
```bash
cat names.txt
# Output:
# alice
# bob
# bob
# charlie

uniq names.txt
# Output:
# alice
# bob
# charlie
```

- *uniq -c* (Count Repeated Lines): Shows how many times each line appears.
Example:
```bash
uniq -c names.txt
# Output:
#   1 alice
#   2 bob
#   1 charlie
```

- *uniq -d* (Only Duplicates): Prints only the lines that are repeated.
Example:
```bash
uniq -d names.txt
# Output:
# bob
```

- *uniq -i* (Ignore Case): Ignores capitalization when comparing lines.
Example:
```bash
printf "Alice\nALICE\n" | uniq -i
# Output:
# Alice
```

Note: `uniq` is most effective when used with `sort`. For example:
```bash
sort names.txt | uniq
```
This sorts the file first, then removes duplicate lines.

### cut [file]: Remove Sections from Each Line of Files
- What it stands for: Cut
- What it does: Extracts specific sections from each line of a file. It is often used to grab columns or parts of text without opening the whole file in a text editor.
- Why use it: Useful when working with CSV style files, logs, or data that is separated by tabs or spaces and you only need one column or section.
- How to use it:
```bash
cat data.txt
# Output:
# alice,30,developer
# bob,25,designer

cut -d ',' -f 1 data.txt
# Output:
# alice
# bob
```

- *cut -d [delimiter] -f [field]* (Custom Delimiter and Field): Chooses a custom separator and extracts a specific column.
Example:
```bash
cut -d ',' -f 2 data.txt
# Output:
# 30
# 25
```

- *cut -c [range]* (Character Range): Extracts a specific character range from each line.
Example:
```bash
echo "hello" | cut -c 1-3
# Output:
# hel
```

- *cut -f [field] --output-delimiter=[delimiter]*: Extracts a field and changes the output separator.
Example:
```bash
cut -d ':' -f 1,3 /etc/passwd
```

Note: `cut` is great for grabbing a single column from structured data. If your file is tab-separated, use `-d '\t'` for the delimiter, and if your file is comma-separated, use `-d ','`.

## 5. Useful Terminal Commands

- [`man`](#man)
- [`history`](#history)
- [`clear`](#clear)
- [`echo`](#echo)
- [`which`](#which)
- [`command -v`](#command--v)

---

## 5.5 Useful Terminal Commands Definitions

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

### echo
- What it does: Prints text or values to the terminal output.
- Why use it: Useful for displaying messages, testing commands, and showing variable values while debugging scripts.
- How to use it:
```bash
echo "Hello, World!"
# Output:
# Hello, World!
```

- *echo $VAR* (Print a Variable): Displays the current value of a variable.
Example:
```bash
name="Bash"
echo $name
# Output:
# Bash
```

- *echo -e* (Enable Escape Sequences): Allows special characters like `\n` and `\t` to be interpreted.
Example:
```bash
echo -e "Line 1\nLine 2"
# Output:
# Line 1
# Line 2
```

Note: `echo` is one of the most basic debugging tools in Bash. It is often used to confirm that a script reached a certain point or to print variable values.

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
