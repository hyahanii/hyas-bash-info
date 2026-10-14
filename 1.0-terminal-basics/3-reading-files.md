# 3 - Reading Files

## Contents

- [`cat`](#cat-file-concatenate-and-display)
- [`less`](#less-file-interactive-file-viewer)
- [`head`](#head-file-display-beginning-of-file)
- [`tail`](#tail-file-display-end-of-file)



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
  - */search_term*: Searches forward for a specific word.
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