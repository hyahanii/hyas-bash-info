# OpenSSL Rand (Standalone Generator)
- while */dev/urandom* requires you to pipe data into other tools, openssl has a built in command that generates random text natively

Example:
```bash
openssl rand -base64 12
```
- what it does: automatically pulls from system entropy and outputs a readable base64 string of a specified byte length in one clean command, without needing *head* or piping

