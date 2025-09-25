# `Hard Links` — GitHub Markdown Cheat Sheet

A beginner-friendly guide for **hard links** in Linux. Useful for study notes, GitHub repos, or CTF/infosec cheat sheets.

---

## Quick Summary

A **hard link** is an additional name for an existing file in the filesystem.  
Unlike a symbolic link, a hard link points directly to the file's **inode**, so the file data remains accessible even if the original file is deleted.

**Key points:**
- Cannot link directories (except root/with special privileges)
- Exists on the same filesystem
- Shares the same inode number with the original file

---

## Syntax

```bash
ln [OPTION] TARGET LINK_NAME
```
# Create a hard link
```
ln file.txt hardlink.txt
```
# Verify both files share the same inode
```
ls -li file.txt hardlink.txt
```
# Create an original file
```
echo "Hello World" > original.txt
```
# Create a hard link to the original file
```
ln original.txt hardlink.txt
```
# View the contents of both files
```
cat original.txt       # Output: Hello World
cat hardlink.txt       # Output: Hello World
```
# Delete the original file
```
rm original.txt
```
# Hard link still retains data
```
cat hardlink.txt       # Output: Hello World
```


<img width="961" height="601" alt="hardlink-softlink" src="https://github.com/user-attachments/assets/e1ad3707-82ae-4690-b73c-42bcc5710cd8" />
