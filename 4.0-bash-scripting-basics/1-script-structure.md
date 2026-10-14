# 4.0 - Script Structure

## Contents

- [`How bash reads a script`](#how-bash-reads-a-script)
  - [`Top-to-bottom execution`](#top-to-bottom-execution)
- [`Interpreter Declaration (shebang)`](#interpreter-declaration-shebang)
  - [`The shebang line`](#the-shebang-line)
  - [`Env path vs absolute path`](#env-path-vs-absolute-path)
- [`File naming and extensions`](#file-naming-and-extensions)
  - [`Extension convention`](#extension-convention)
  - [`Execution permissions`](#execution-permissions)
  - [`Execution methods`](#execution-methods)
- [`Script exit points`](#script-exit-points)
  - [`Explicit exit and status codes`](#explicit-exit-and-status-codes)

## How bash reads a script

### Top-to-bottom execution
- What it is: Bash reads and executes commands sequentially, line by line, from top to bottom.
- Why it matters: Execution order determines program logic. Commands run in the exact sequence they appear in the file.

- Example:
```bash
#!/usr/bin/env bash

echo "First line"
echo "Second line"
```
## Interpreter Declaration (shebang)

### The shebang line
- What it is: The first line of a script starting with `#!` followed by the path to the interpreter.
- Why it matters: It tells the operating system which program to use to execute the script file. Without it, the system won't know how to parse the commands.

- Example:
```bash
#!/usr/bin/env bash
```

### Env path vs absolute path
- What it is: The difference between using `#!/usr/bin/env bash` and `#!/bin/bash`. The env approach searches the system PATH variable to locate bash dynamically, while the absolute path hardcodes a specific system location.
- Why it matters: Using env makes scripts more portable across different Unix systems where bash might be installed in different directories. Hardcoding assumes a fixed path.

- Example:
```bash
# Dynamic lookup (portable)
#!/usr/bin/env bash

# Hardcoded absolute path
#!/bin/bash
```

## File naming and Extensions

### Extension convention
- What it is: The standard practice of appending `.sh` to the end of a script filename.
- Why it matters: It visually identifies the file as a shell script for users and text editors, though the operating system relies on permissions and the shebang line rather than the file extension to execute it.

- Example:
```bash
# Standard naming convention
myscript.sh
```

### Execution permissions
- What it is: The file permission setting that allows the operating system to execute a file as a program.
- Why it matters: Even with a correct shebang, a script cannot be run directly from the terminal until the executable bit is set.

- Example:
```bash
chmod +x myscript.sh
./myscript.sh
## Script exit points
```

### Execution methods
- What it is: Running a script by passing the filename directly to the bash interpreter versus executing it as a standalone program.
- Why it matters: Passing the file to bash (`bash filename.sh`) forces the shell interpreter to read and run it, which bypasses the need for the file to have execution permissions (`+x`) or a shebang line.

- Example:
```bash
# Runs without +x permissions or shebang
bash myscript.sh

# Requires +x permissions and a shebang line
./myscript.sh
```

### Explicit exit and status codes
- What it is: The termination of script execution, either reaching the final line automatically or using the exit command with a numeric status code.
- Why it matters: Exit codes communicate success or failure back to the calling shell or automation pipeline, allowing other programs or scripts to check if the script ran correctly.

- Example:
```bash
#!/usr/bin/env bash

echo "Processing data..."
# Exit with a success status code
exit 0
```