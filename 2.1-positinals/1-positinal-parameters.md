## Positional Parameters

Positional parameters are special built in variables that hold the arguments passed to a script or a function from the command line. They are ordered sequentially based on the order you type them.

## Key Positional Variables

- **`$0`**: The name of the script itself.
- **`$1`**, **`$2`**, **`$3`**...: The first, second, third argument passed to the script, respectively.
- **`$#`**: Returns the total number of arguments passed.
- **`$@`**: Represents all the arguments as separate strings.
- **`$?`**: Returns the exit status of the last executed command (0 for success, non-zero for error).
- **`$$`**: Returns the Process ID (PID) of the current shell script.
- **`$!`**: Returns the Process ID (PID) of the most recently executed background job.

## Example Usage

If you have a script named `greet.sh`:

```bash
#!/bin/bash

echo "Hello, $1!"
echo "Welcome to $2."
echo "You passed $# total arguments."
```

## Accessing Double-Digit Positional Parameters

When you pass more than nine arguments to a script, you run into a parsing quirk in Bash. 

If you try to access the tenth argument by writing `$10`, Bash will actually read it as **`$1` followed by a literal `0`** (meaning it outputs the first argument, then appends a zero).

## Using Curly Braces

To tell Bash to look at the full two-digit number, you must wrap the index in curly braces:

```bash
#!/bin/bash

echo "The tenth argument is: ${10}"
```

## The `shift` Command

When a script accepts an unknown or variable number of arguments, dealing with them one by one using `$1`, `$2`, etc., can get messy. The `shift` command moves all positional parameters to the left by one index.

* `$1` is discarded.
* `$2` becomes the new `$1`.
* `$3` becomes the new `$2`, and so on.

### Example of `shift` in a Loop

```bash
#!/bin/bash

# Loop as long as there are arguments left ($# is greater than 0)
while [[ $# -gt 0 ]]; do
    echo "Processing argument: $1"
    shift # Move to the next argument
done
```