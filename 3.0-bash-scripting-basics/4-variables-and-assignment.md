# Variables and Assignment

- To assign a value to a variable, you just give it a name and set it equal to a value.

Example:
```bash
name="hya"
number=69420
```

**One rule**: No spaces allowed around the = sign!
- name="hya" works
- name = "hya" will error because Bash thinks name is a command.



## Accessing Variables (Using Them)

- To read or use the value stored inside a variable, you put a dollar sign ($) right in front of its name.

Example: 
```bash
name="hya"
echo "Hello $name!!"
# Output: Hello hya!!
```



## Double Quotes vs. Single Quotes

- **Double Quotes** ("..."): Allow variable expansion. Bash will look inside the string, spot the $, and swap it out for the actual variable value.
- **Single Quotes** ('...'): Treat everything literally. Bash will ignore the $ and print the exact text you put in there.

```bash
name="hya"

# Double quotes expand the variable
echo "Hello, $name"
# Output: Hello, hya

# Single quotes treat it like plain text
echo 'Hello, $name'
# Output: Hello, $name
```


### Storing Command Outputs

- You can also assign the output of a shell command directly into a variable using command substitution (using parentheses with a dollar sign):

```bash
current_directory=$(pwd)
echo "You are currently in: $current_directory"
```