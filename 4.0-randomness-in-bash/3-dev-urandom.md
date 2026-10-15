# 3 /dev/urandom

- it is a special system file that outputs true random bytes sourced from the operating systems environmental noise, just like /dev/random
- unlike /dev/random, it is *non-blocking*, meaning it will never pause execution or freeze your script if the system runs low on physical entropy

Example:
```bash
head -c 10 /dev/urandom
```

- this reads 10 random bytes from the /dev/urandom file safely in the background

Practical Example:
```bash
head -c 100 /dev/urandom | base64 | tr -dc 'a-zA-Z0-9' | head -c 12
```
what it does: pulls 100 raw random bytes non-blockingly from /dev/urandom, converts them to base64 text, strips out everything except letters and numbers using *tr -dc*, and makes the final result down to exactly 12 characters

