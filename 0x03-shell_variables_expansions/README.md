# Shell, init files, variables and expansions

This project focuses on the fundamentals of shell scripting in Ubuntu, specifically working with shell initialization files, variables, and expansions. I will be creating small, efficient Bash scripts that follow strict formatting rules: exactly two lines long, beginning with a `#!/bin/bash` shebang, ending with a newline, and being executable.

## Task: 0-alias

**Description:**  
Create a script that defines a shortcut (alias) in the shell.

- **Name:** `ls`  
- **Value:** `rm *`

**Solution (0-alias):**
```bash
#!/bin/bash
alias ls='rm *'

## Task:  1-hello_you

**Description:**
Create a script that prints hello user, where user is the current Linux user.
**Solution (1-hello_you):**
```bash
#!/bin/bash
echo "hello $USER"
