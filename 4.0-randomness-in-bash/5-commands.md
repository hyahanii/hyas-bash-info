# Commands

- **head -c [number]**: limits the number of random bytes you pull from the file

- **base64**: converts raw random bytes into standard readable text (letters, numbers, *+* and */*) 

- **tr** (translate/delete): can be used to strip out characters you dont want or filter down to specific letters and numbers

- **tr -dc** (complement and delete): deletes everything except the specific characters you list (e.g., *tr -dc 'a-zA-Z0-9'* acts as a strict whitelist to keep only letters and numbers)

- **fold**: when you use *base64* on random bytes, it sometimes spits out a log block of text, the *fold* command can wrap or cut text at a specific column width

example: 
```bash
head -c 50 /dev/urandom | base64 | fold -w 10 | head -n 1
```
what it does: grabs bytes, turns them into base64 text, folds (wraps) the text every 10 characters, and grabs just the first line

- **uuidgen** (unique ID generator)
what it does: it creates a completely random, globally unique string of letters, numbers, and dashes (for example: 123e4567-e89b-12d3-a456-426614174000)
why its cool: you dont need to pipe it into anything or set up a complicated command, you just type uuidgen, and it instantly spits out a random ID that is guaaranteed to be unique

example:
```bash
uuidgen
```

- **shuf** (shuffle)
what it does: it takes text or lines and completely randomizes their order

example: 
```bash
shuf -e apple banana cherry date
```
what this does: picks the items you list and randomly shuffles their order every time you run it (or you can use it to shuffle text files line by line)