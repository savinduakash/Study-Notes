# `find` — GitHub Markdown Cheat Sheet

A beginner-friendly guide for the Linux `find` command. Useful for study notes, GitHub repos, or CTF/infosec cheat sheets.

---

## Quick Summary

The `find` command is used to **search for files and directories** in a directory hierarchy based on name, type, size, permissions, timestamps, and more.  
It is extremely powerful for **system administration, scripting, and cybersecurity tasks**.

**Key points:**
- Recursively searches directories
- Can filter by name, type, size, permissions, timestamps
- Supports executing commands on matched files

---

## Syntax

```bash
find [PATH...] [OPTIONS] [EXPRESSION]

PATH = starting directory (default is current directory .)
OPTIONS/EXPRESSION = search criteria (name, type, size, etc.)
```

## Basic Usage

```bash
# Find a file by name in current directory and subdirectories
find . -name "file.txt"

# Find all .txt files in /home/user
find /home/user -type f -name "*.txt"

# Find all directories named "backup"
find / -type d -name "backup"

# Find files by size (>1MB)
find . -type f -size +1M
```

## Examples

```bash
# Delete all .tmp files (careful!)
find /tmp -type f -name "*.tmp" -exec rm {} \;

# Find files modified in the last 7 days
find /var/log -type f -mtime -7

# Find empty files
find . -type f -empty

# Find files with specific permissions (e.g., SUID)
find / -type f -perm -4000 2>/dev/null

# Combine multiple conditions: find .txt or .log files
find . \( -name "*.txt" -o -name "*.log" \)

# Search for files by name (case-insensitive)
find /usr -iname gcc

# Find files larger than 100MB
find /var/log -size +100M

# Find files accessed more than 7 days ago
find /tmp -atime +7

# Find and list file details
find . -type f -exec ls -lh {} \;

# Find all symbolic links
find / -type l
```

## Options

| Option/Expression | Example | Meaning |
|-------------------|---------|---------|
| `-name` | `find . -name "*.txt"` | Search by filename pattern |
| `-iname` | `find . -iname "*.txt"` | Case-insensitive filename search |
| `-type` | `find . -type f` | f = file, d = directory, l = symlink |
| `-size` | `find . -size +1M` | Find files by size (+ larger, - smaller) |
| `-perm` | `find . -perm 644` | Find files with specific permissions |
| `-mtime` | `find . -mtime -7` | Modified in last 7 days |
| `-atime` | `find . -atime +7` | Accessed more than 7 days ago |
| `-user` | `find /home -user root` | Files owned by a user |
| `-group` | `find /var -group staff` | Files belonging to a group |
| `-empty` | `find . -empty` | Find empty files or directories |
| `-exec` | `find . -name "*.log" -exec rm {} \;` | Execute a command on matched files |
| `-print` | `find . -name "*.txt" -print` | Print the matching files (default behavior) |

## Practical Examples

```bash
# Clean old temporary files (older than 10 days)
find /tmp -type f -atime +10 -exec rm {} \;

# Search for large log files (>50MB)
find /var/log -type f -size +50M

# Find SUID binaries (security audit)
find / -type f -perm -4000 2>/dev/null

# Find world-writable files (security risk)
find / -type f -perm -002 2>/dev/null

# Find files owned by a specific user
find /home -user john -type f

# Find configuration files
find /etc -name "*.conf" 2>/dev/null

# Find recently modified files (last 24 hours)
find . -type f -mtime -1
```

## Tips

- Redirect errors to avoid permission denied messages:

```bash
find / -name "*.conf" 2>/dev/null
```

- Combine find with grep to filter results:

```bash
find /var/log -type f | grep "auth"
```

- Use parentheses `\(...\)` with `-o` for logical OR operations (escape required in shell).
- Always test commands like `-exec rm` carefully to avoid accidental deletion.
- Use `-maxdepth` to limit search depth: `find . -maxdepth 2 -name "*.txt"`

## Quick Reference

```bash
find . -name "file.txt"              # search by name
find . -iname "file.txt"             # case-insensitive name search
find /path -type f                   # find files
find /path -type d                   # find directories  
find /path -type l                   # find symbolic links
find . -size +1M                     # files larger than 1MB
find . -size -1K                     # files smaller than 1KB
find . -perm 644                     # files with permissions 644
find . -mtime -7                     # modified in last 7 days
find . -atime +30                    # accessed more than 30 days ago
find . -user root                    # files owned by root
find . -group staff                  # files belonging to staff group
find . -empty                        # find empty files/directories
find . -name "*.tmp" -exec rm {} \;  # execute command on results
```

---

*Created: 2025-09-25*
