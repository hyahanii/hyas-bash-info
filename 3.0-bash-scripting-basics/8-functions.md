# 8 Functions

A function is a reusable block of code. Instead of writing the same lines over and over again in your script, you write them once inside a function and "call" them whenever you need them. 

Think of it like a custom command you invent for your script.

## Defining and Calling a Function

You can define a function using either the `function` keyword or just parentheses. The standard, most common way is using parentheses right after the function name:

```bash
# Defining the function
say_hello() {
    echo "Hello, welcome to the game!"
}

# Calling the function (just use its name, NO parentheses)
say_hello
```

Rule: You must define a function before your script tries to call it. Bash reads files from top to bottom.