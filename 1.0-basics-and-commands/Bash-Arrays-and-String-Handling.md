# Bash Arrays and String Handling

## Contents

- [Strings](#strings)
- [String operations](#string-operations)
- [Indexed arrays](#indexed-arrays)
- [Working with arrays](#working-with-arrays)
- [Associative arrays](#associative-arrays)
- [Quoting and safe expansion](#quoting-and-safe-expansion)
- [Common mistakes](#common-mistakes)

This chapter covers how Bash stores and works with text and collections of values.

---

## Strings

- What a string is in Bash
- Storing text in variables
- Empty strings and strings containing spaces
- Bash does not have a separate integer variable type; values are stored as text unless used in an arithmetic context

## String operations

- Getting the length of a string
- Extracting part of a string
- Replacing text with parameter expansion
- Removing matching prefixes or suffixes
- Distinguishing string operations from external text-processing commands

## Indexed arrays

- What an indexed array is and when to use one
- Creating arrays
- Zero-based indexes
- Reading or updating one element
- Handling indexes that have not been assigned

## Working with arrays

- Getting the number of elements
- Expanding all elements with `"${array[@]}"` and `"${array[*]}"`
- Appending elements
- Removing elements
- Looping through array elements
- Preserving spaces and empty elements

## Associative arrays

- What key-value arrays are
- Declaring an associative array
- Setting and reading values by key
- Listing keys and values
- Bash version requirements and portability notes

## Quoting and safe expansion

- Why array and string expansions should usually be quoted
- The difference between `"$var"`, `"${array[@]}"`, and `"${array[*]}"`
- How unquoted expansions can split text or expand wildcard characters
- Passing array elements safely as separate command arguments

## Common mistakes

- Adding spaces around `=` in an assignment
- Using the wrong array expansion form
- Forgetting that array indexes start at zero
- Assuming a variable preserves multiple words as separate values
- Confusing Bash built-in string operations with commands such as `cut`, `sed`, or `awk`
