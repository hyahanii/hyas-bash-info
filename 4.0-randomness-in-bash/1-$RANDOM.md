# $RANDOM

- It can generate a pseudo random number between 0 - 32767

Example use:
```bash
echo $RANDOM
echo $RANDOM
```

- This will generate 2 random numbers between 0 - 32767

## range
- you can create a set range for $RANDOM by using modulo operator e.g. 

```bash
echo $(( RANDOM % 50 ))
echo $(( RANDOM % 10 ))
```
- This prints out 2 numbers ranging from 0-49 and 0-9

## Shifting the range
- if you dont want a range of 0 - 9 and want 1 - 10 for example you can use 

```bash
echo $(( ($RANDOM % 10) +1 ))
echo $(( ($RANDOM % 50) +1 ))
```
- in these examples it prints out a random number between 1 - 10 or 1 - 50

## The seeding quirk (predictable randomness)

- bash uses a seed value to calculate its pseudo random sequence automatically from the system clock
- if you manually set the variable like RANDOM=1, bash will use that exact number to start its math sequence, causing your script to generate the exact same sequence of random numbers every single time you run it
- this is useful for seed-based games (like world generation) where players can replay the exact same layout, but you should avoid hardcoding it unless you want predictable results

example:
```bash
RANDOM=50
echo $RANDOM
echo $RANDOM
```
- This outputs 21138 and 19151 every single time in the exact same order every time it is ran. 