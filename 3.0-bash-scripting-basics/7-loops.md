# 7 Loops

## Contents

- [`for loop`](#for-loop)
- [`until loop`](#until-loop)
- [`while loop`](#while-loop)

### What is a loop?
Imagine you need to say "Hello" to five different friends. Without a loop, you would have to write out:
```bash
echo "Hello, hya"
echo "Hello, Bob"
echo "Hello, Charlie"
echo "Hello, David"
echo "Hello, Emma"
```

That gets repetitive very quickly, especially if you had 500 friends!

A loop is a shortcut that automates repetition. Instead of writing the same command over and over, you write it once and tell the computer to repeat it automatically until a specific condition is met or a list of items runs out. It turns manual busywork into a quick, automated process.


### for loop
The for loop iterates over a list of items, a sequence, or an array, executing the code block once for each item.

Example:
```bash
for ITEM in apple banana cherry; do
    echo "Current fruit: $ITEM"
done
# Output: 
# Current fruit: apple
# Current fruit: banana
# Current fruit: cherry
```

### while loop
The while loop continuously executes a block of code as long as the specified condition evaluates to true.

Example:
```bash
COUNT=1
while [[ $COUNT -le 3 ]]; do
    echo "Count is: $COUNT"
    (( COUNT++ ))
done
# Output:
# Count is: 1
# Count is: 2
# Count is: 3
```

### until loop
The until loop is the opposite of a while loop. It continuously executes a block of code until the specified condition becomes true (meaning it keeps running as long as the condition evaluates to false).

```bash
COUNT=1
until [[ $COUNT -gt 3 ]]; do
    echo "Waiting... Count is: $COUNT"
    ((COUNT++))
done
# Output:
# Waiting... Count is: 1
# Waiting... Count is: 2
# Waiting... Count is: 3
```