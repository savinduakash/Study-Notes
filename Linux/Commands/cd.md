# Linux Command Learning Package: `cd`


---

## Overview

- `cd` (change directory) is a shell built-in command.  
- It changes the current working directory in Bash, Zsh, or any POSIX shell.  

---

## Options

| Option | Description |
|--------|-------------|
| `-L`   | Follow symbolic links (default). |
| `-P`   | Use physical directory structure; do not follow symlinks. |
| `-e`*  | With `-P`, exit with error if directory cannot be determined. |
| `-`    | Go to previous directory (`$OLDPWD`) and print path. |
| No argument | Go to home directory (`$HOME`). |

\* Bash-specific.

---

## Examples<img width="1772" height="848" alt="Screenshot from 2025-09-04 09-05-11" src="https://github.com/user-attachments/assets/0976a19f-1355-483f-8c36-86c2b7c281f3" />


### Setup

#### Create a sandbox directory
``` bash
mkdir -p ~/cd_lab/{real1,real2}
cd ~/cd_lab
```
## Create symbolic link
ln -s real1 mylink

# Save current directory
echo "HOME_DIR=$(pwd)" > setup_env.sh



