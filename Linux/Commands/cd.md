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

## Examples

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


