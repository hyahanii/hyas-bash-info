# 5.0 - Conditionals and Loops

## Contents

- [`Conditionals`](#conditionals)
  - [`If/Else statements`](#ifelse-statements)
  - [`Case statements`](#case-statements)
- [`Loops`](#loops)
  - [`For loops`](#for-loops)
  - [`While loops`](#while-loops)
  - [`Until loops`](#until-loops)

## Conditionals

### If/Else statements

#### The `if` statement
- What it does: Evaluates a cndition. If the condition returns a success exit status (true), the code block inside the `then` section executes.
- Why it matters: It is the foundation of script logic, allowing code to make its first core decision.

#### The `elif` (else if) statement
- What it does: Evaluates an alternative condition only if the preceding `if` (or previous `elif`) statement evaluates to false.
- Why it matters: It allows you to handle multiple distinct conditions cleanly without writing deeply nested `if` statements.

#### The `else` statement
- What it does: Acts as a catch-all fallback. It executes its code block only if all preceding `if` and `elif` conditions fail.
- Why it matters: It ensures your script always has a default behavior or error-handling path when no specific conditions match.

- Example:
```bash
# Check system status or user input
if [ "$1" = "start" ]; then
    echo "Starting service..."
elif [ "$1" = "stop" ]; then
    echo "Stopping service..."
elif [ "$1" = "restart" ]; then
    echo "Restarting service..."
else
    echo "Usage: $0 {start|stop|restart}"
    exit 1
fi
```


### Case statements

#### The pattern matching blocks
- What it does: Compares the target variable against specific literal strings or glob patterns (e.g., `start)`, `stop|restart)`), executing the matching code block.
- Why it matters: It allows you to match multiple distinct values or alternative options cleanly within a single branch structure.

#### The double semicolon `;;`
- What it does: Terminates the code block for a specific pattern match, preventing the shell from falling through and executing subsequent patterns.
- Why it matters: Unlike some other programming languages, Bash requires an explicit break command (`;;`) so that only one matched block runs.

#### default pattern `*`
- What it does: Acts as a catch all fallback matching any input that failed to match all previous patterns.
- Why it matters: It ensures your script handles unexpected or invalid input safely, making it ideal for error handling or usage prompts.

#### The `esac` keyword
- What it does: Marks the end of the entire `case` block (spelled `case` backwards).
- Why it matters: It is a required syntax element that tells the shell where the conditional structure concludes.

- Example:
```bash
# Multi-way branch selection using a case statement
case "$1" in
    start)
        echo "Starting the application..."
        ;;
    stop|restart)
        echo "Stopping or restarting the application..."
        ;;
    *)
        echo "Usage: $0 {start|stop|restart}"
        exit 1
        ;;
esac
```


## Loops

### For loops

#### The iteration list (`in item1 item2 ...`)
- What it does: Defines the set of values, items, or files that the loop will iterate through one by one.
- Why it matters: It allows you to process collections of data sequentially without manually writing separate commands for each item.

#### The loop variable (`variable`)
- What it does: Holds the current item's value during each individual iteration of the loop.
- Why it matters: It gives you a dynamic reference to the item currently being processed inside the loop block.

#### The `do` and `done` keywords
- What it does: Mark the beginning (`do`) and end (`done`) of the code block that executes on every iteration.
- Why it matters: They define the scope of the repetitive actions performed by the loop.

- Example:
```bash
# Iterate through a list of server names
SERVERS=("web1" "web2" "db1")

for server in "${SERVERS[@]}"; do
    echo "Connecting to $server..."
done
```


## Loops

### For loops

#### The iteration list (`in item1 item2 ...`)
- What it does: Defines the set of values, items, or files that the loop will iterate through one by one.
- Why it matters: It allows you to process collections of data sequentially without manually writing separate commands for each item.

#### The loop variable (`variable`)
- What it does: Holds the current item's value during each individual iteration of the loop.
- Why it matters: It gives you a dynamic reference to the item currently being processed inside the loop block.

- Example:
```bash
# Iterate through a list of server names
SERVERS=("web1" "web2" "db1")

for server in "${SERVERS[@]}"; do
    echo "Connecting to $server..."
done
```


### While loops

#### The condition
- What it does: Evaluates a test condition before each iteration. If the condition is true, the loop executes its block; if false, the loop terminates.
- Why it matters: It allows you to run a block of code an unknown number of times until a specific runtime condition changes (e.g., waiting for a service to start or reading a file line-by-line).

#### The `do` and `done` keywords
- What it does: Define the boundaries of the block that repeats as long as the test condition remains true.
- Why it matters: They encapsulate the iterative logic cleanly so the shell knows what code to execute on each cycle.

- Example:
```bash
# Count down from 3
count=3
while [ $count -gt 0 ]; do
    echo "Countdown: $count"
    ((count--))
done
echo "Blast off!"
```


### Until loops

#### The condition (inverse logic)
- What it does: Evaluates a test condition before each iteration, running the loop block *only while* the condition is false, and terminating when it finally becomes true.
- Why it matters: It provides the logical inverse of a while loop, which is ideal when waiting for a specific event, file creation, or system state change to occur.

#### The `do` and `done` keywords
- What it does: Define the boundaries of the repetitive block of code executed during each cycle.
- Why it matters: They structure the loop so the shell knows precisely which commands to repeat until the termination condition is met.

- Example:
```bash
# Count up until reaching 3
count=0
until [ $count -eq 3 ]; do
    echo "Current count: $count"
    ((count++))
done
echo "Target reached!"
```