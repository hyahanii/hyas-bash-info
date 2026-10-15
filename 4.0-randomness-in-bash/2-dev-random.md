# /dev/random

- it is a special system file that outputs true random bytes sourced from the operating systems environmental noise (hardware events, driver timings, and system activity).

- unlike $RANDOM, which uses a mathematical formula to generate pseudo random numbers, /dev/random provides true cryptographic randomness.

Example:

```bash
head -c 10 /dev/random
```
- this reads 10 random bytes from the /dev/random file

- **note:** because these are raw system bytes, printing them directly will often output weird symbols or unprintable characters

## tools used with it (to make it readable)
- since raw bytes from */dev/random* arent clean numbers or letters, you can pipe them into filtering tools:

```bash
head -c 10 /dev/random | base64
```
- *head -c [number]*: limits the number of random bytes you pull from the file
- *base64*: converts raw random bytes into standard readable text (letters, numbers, *+* and */*) 

## the blocking quirk (the catch)
- because */dev/random* relies on real world physical chaos, it maintains a pool of available random data known as "entropy"

- if your system runs low on entropy, */dev/random* will pause execution (block) and freeze your script until it can gather enough new environmental noise

- because of this freezing behavior, prefer to use its sister file, /dev/urandom, for things like scripts and password generators.