# `mv` — GitHub Markdown Cheat Sheet

A beginner-friendly guide for the Linux `mv` command. Useful for study notes, GitHub repos, or CTF/infosec cheat sheets.

---

## Quick Summary

The `mv` command is used to **move or rename files and directories** in Linux.  
It does **not create copies**; the original file is removed from the source location after moving.

**Key points:**
- Can rename files or directories
- Can move files across directories
- Supports overwriting and interactive prompts

---

## Syntax

```bash
mv [OPTIONS] SOURCE TARGET

SOURCE = file or directory to move/rename
TARGET = destination file/directory name
```

## Basic Usage

```bash
# Rename a file
mv oldname.txt newname.txt

# Move a file to another directory
mv file.txt /path/to/destination/

# Rename a directory
mv oldfolder newfolder
```

## Example

```bash
# Create a sample file
echo "Hello MV" > file.txt

# Rename the file
mv file.txt renamed.txt

# Move the file to another directory
mkdir testdir
mv renamed.txt testdir/

# Move and rename in one step
mv testdir/renamed.txt testdir/final.txt
```

## Options

| Option | Example | Meaning |
|--------|---------|---------|
| `-i` | `mv -i file.txt dest/` | Interactive mode (ask before overwrite) |
| `-f` | `mv -f file.txt dest/` | Force overwrite without prompt |
| `-u` | `mv -u file.txt dest/` | Move only if source is newer than dest |
| `-v` | `mv -v file.txt dest/` | Verbose; show what is being moved |

## Tips

- Combine with wildcards to move multiple files:

```bash
mv *.txt /path/to/destination/
```

- Use `-i` to avoid accidental overwrites, especially in scripts.
- To move directories, the same syntax applies as for files.

## Quick Reference

```bash
mv oldname.txt newname.txt     # rename file
mv file.txt /path/to/dir/      # move file
mv -i file.txt /dest/          # interactive mode
mv -f file.txt /dest/          # force overwrite
mv -v file.txt /dest/          # verbose output
mv *.txt /dest/                # move multiple files
```



<img width="962" height="1080" alt="mv" src="https://github.com/user-attachments/assets/4a3dbcea-f664-4572-977c-94ecaf602653" />

