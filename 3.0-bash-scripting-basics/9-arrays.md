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

## Adding Elements to an Array

You can add new items to an existing array dynamically using the `+=` assignment operator combined with parentheses:

```bash
# Initializing an array
FRUITS=(apple banana)

# Adding a single item to the end of the array
FRUITS+=(cherry)

# Adding multiple items at once
FRUITS+=(date elderberry)

echo "${FRUITS[@]}"  # Output: apple banana cherry date elderberry
```

You can combine the `read` command with the array assignment operator (`+=`) to let users dynamically add items to an array at runtime:

```bash
# Initialize an empty array for our tasks
TASKS=()

# Prompt the user to input data and store it in a variable
read -p "Enter a new task: " new_task

# Add the variable's value to the array using double quotes for safety
TASKS+=("$new_task")

# Verify it was added
echo "Current tasks: ${TASKS[@]}"
```