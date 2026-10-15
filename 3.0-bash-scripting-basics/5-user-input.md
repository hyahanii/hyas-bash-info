# 5 User Input

## read
- stands for reading user input (or just grabbing whatever the user types into the terminal)
- unlike just running a script on autopilot, read pauses the script and waits for the user to type something and hit Enter

```bash
echo "What is your name?"
read name
echo "Hello, $name!"
```

this pauses the script right at *read name*, waits for you to type your name, saves whatever you typed into the $name variable, and then prints it right back out

## flags and options

instead of just grabbing raw input blindly, read has flags to help you control how it behaves
- **-p**: lets you show a prompt inline without needing a separate echo line first
- **-s**: silent mode (hides what you're typing, super useful for passwords so it doesn't display on the screen)

Example:
```bash
read -p "Enter your username: " username
read -s -p "Enter your password: " password
echo ""
printf "\nThanks! Logged in as %s\n" "$username"
```

What it does: prompts you for your username right on the same line, then asks for your password while hiding your keystrokes with -s, drops a newline with a blank echo, and then prints a clean confirmation using printf!