# Linux Command Learning Package: `cd`

A complete guide to the Linux `cd` command with **options, examples, lab practice, and tips**.

---

## Table of Contents

1. [Overview](#overview)
2. [Options](#options)
3. [Examples](#examples)
4. [Lab Worksheet](#lab-worksheet)
    - [Setup](#setup)
    - [Command-Line Practice](#command-line-practice)
    - [Interactive Practice](#interactive-practice)
    - [Cleanup](#cleanup)
5. [Task Submission](#task-submission)
6. [Summary](#summary)
7. [Tips & Tricks](#tips--tricks)

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

### 1. cd -L (logical)
```bash
ln -s /usr /tmp/linktousr
cd -L /tmp/linktousr
pwd
# Output: /tmp/linktousr
