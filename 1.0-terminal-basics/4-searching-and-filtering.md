# 1.0 - Searching and Filtering

## Contents

- [`grep`](#grep-pattern-file-global-regular-expression-print)
- [`find`](#find-dir-criteria-find-files-and-directories)
- [`wc`](#wc-file-word-count)
- [`sort`](#sort-file-sort-lines-of-text-files)
- [`uniq`](#uniq-file-report-or-omit-repeated-lines)
- [`cut`](#cut-file-remove-sections-from-each-line-of-files)

## Searching and filtering commands

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