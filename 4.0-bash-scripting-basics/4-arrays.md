# 4.0 - Arrays

## Contents

- [`Indexed arrays`](#indexed-arrays)
- [`Associative arrays`](#associative-arrays)
- [`Array operations`](#array-operations)

## Indexed arrays

### Defining and accessing arrays
- What it is: A way to store multiple values in a single variable, referenced by a numeric index starting at zero.
- Why it matters: It lets you group related data together (like a list of filenames or configuration items) instead of creating a separate variable for every single item.

- Example:
```bash
# Define an indexed array
USERS=("Alice" "Bob" "Charlie")

# Access specific elements by index
echo "${USERS[0]}" # Prints Alice
echo "${USERS[2]}" # Prints Charlie

# Print all elements
echo "${USERS[@]}"
```

## Associative arrays

### Defining and accessing associative arrays
- What it is: A collection of data stored as key-value pairs rather than numeric indices, where each value is looked up using a custom string key.
- Why it matters: It lets you map names or identifiers directly to data (like configuration settings or user metadata) without needing to remember numeric positions.

- Example:
```bash
# Declare an associative array (required before assignment)
declare -A USER_ROLES

# Assign key-value pairs
USER_ROLES["Alice"]="Admin"
USER_ROLES["Bob"]="Editor"

# Access values by their string key
echo "${USER_ROLES["Alice"]}" # Prints Admin
```

## Array operations

### Length and adding items
- What it is: Built-in syntax to check how many items are in an array or append new data dynamically.
- Why it matters: It allows scripts to handle lists of varying sizes without hardcoding limits.

- Example:
```bash
# Get the total number of items
echo "${#USERS[@]}"

# Append a new item to the array
USERS+=("Diana")
echo "${USERS[@]}"
```