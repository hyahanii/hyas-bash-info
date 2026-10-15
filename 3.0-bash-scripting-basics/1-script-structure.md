# 1 - Script Structure

## Contents

- [`Shebang`](#shebanghashbang)
- [`File extension`](#file-extensions)
- [`Executable permissions`](#executable-permissions)

## Shebang/Hashbang
- Meaning: The character sequence `#!` located at the very first line of an executable script, followed by the absolute path to the interpreter that should process the file.
- Role in execution: Tells the operating system which interpreter (such as `/bin/bash`, `/bin/sh`, or `/usr/bin/env python3`) to launch to execute the script's code when run directly as an executable.

Example:
```bash
#!/bin/bash
echo "Running with Bash!"
```

Preferd shebang Example:
```bash
#!/usr/bin/env bash
echo "Running with Bash!"
```



## File Extensions
- Meaning: A suffix appended to the end of a filename (such as `.sh` for Bash scripts) that indicates the file type or format.
- Role in execution: Unlike some operating systems, Linux and Bash do not strictly rely on file extensions to execute files. Execution is determined by the shebang line and executable permissions (`chmod +x`). However, extensions are widely used as a helpful convention for humans, text editors, and package managers to identify file contents.

Example:
```bash
# Both a file named "script" and "script.sh" will run the exact same way 
# as long as they have a shebang and executable permissions.
./script.sh
# Output: Executes successfully based on the shebang and permissions, not the .sh extension.
```



## Executable Permissions
- Meaning: Permission flags associated with a file that grant users (the owner, group, or others) the right to run the file as a program or script.
- Role in execution: The operating system checks these permissions before allowing a file to run. Even if a script has a valid shebang and proper syntax, the system will block execution with a "Permission denied" error unless executable permissions are explicitly granted using `chmod +x`.

- Example:
```bash
# Grant executable permission to the script
chmod +x myscript.sh

# Run the script directly
./myscript.sh
# Output: Executes the script successfully
```

# Alternatively, run without executable permissions by passing it to the interpreter
```bash
bash myscript.sh
# Output: Executes the script successfully without needing chmod +x
```