## 9 Arrays

An array is a variable that can store multiple values instead of just one. It allows you to group a list of items together under a single name.

## Declaring and Initializing an Array

You create an array by wrapping items in parentheses and separating them with spaces:
```bash
# Declaring an array of items
FRUITS=(apple banana cherry)
```

## Accessing Elements

Bash arrays are zero-indexed, meaning the first item starts at index 0. You access individual elements using their index number inside square brackets:

```bash
echo "${FRUITS[0]}"  # Output: apple
echo "${FRUITS[1]}"  # Output: banana
echo "${FRUITS[2]}"  # Output: cherry
```

## Useful Array Operations

- Get all elements: ${FRUITS[@]} references every item in the array.
- Get array length: ${#FRUITS[@]} returns the total number of items stored in the array.

Example of iterating through an array with a loop:
```bash
#!/bin/bash

FRUITS=(apple banana cherry)

for ITEM in "${FRUITS[@]}"; do
    echo "Current item: $ITEM"
done
```