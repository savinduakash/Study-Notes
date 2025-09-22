# `cat` — GitHub Markdown Cheat Sheet

A simple, beginner-friendly guide for the Linux `cat` command. Useful for study notes, GitHub repos, or CTF/infosec cheat sheets.

---

## Quick summary

`cat` = **concatenate**. Reads, shows, or combines files. Can also create or append to files.

**Syntax:**

```bash
cat [OPTIONS] [FILE...]
```

---

## 🔹 Basic Usage

```bash
# Show a file
cat file.txt

# Show multiple files
cat file1.txt file2.txt

# Combine multiple files into a new file
cat file1.txt file2.txt > combined.txt
```

---

## 🔹 Create a file

```bash
cat > notes.txt
Type your text here
Press Ctrl+D to save
```

## 🔹 Append text to a file

```bash
cat >> notes.txt
Add extra lines
Press Ctrl+D to save
```

---

## 🔹 Useful Options

| Option | Example           | Meaning                      |
| ------ | ----------------- | ---------------------------- |
| `-n`   | `cat -n file.txt` | Number all lines             |
| `-b`   | `cat -b file.txt` | Number non-empty lines       |
| `-s`   | `cat -s file.txt` | Squeeze multiple blank lines |
| `-E`   | `cat -E file.txt` | Show `$` at the end of lines |
| `-T`   | `cat -T file.txt` | Show tabs as `^I`            |

---

## 🔹 Security / Cybersec Uses

```bash
# View sensitive system files
cat /etc/passwd
cat /etc/shadow  # if permissions allow

# Read SSH keys
cat ~/.ssh/id_rsa

# Grab flags in CTFs
cat flag.txt

# Check logs for suspicious activity
cat /var/log/auth.log | grep "failed"
```

---

## 🔹 Tips

* Combine with `less` for big files:

```bash
cat bigfile.log | less
```

* `tac` = reverse of `cat` (prints bottom-up).
* Use in scripts for concatenating files or pipelines.

---

## 🔹 Quick reference

```
cat file.txt        # show file
cat file1 file2     # show multiple files
cat file1 file2 > newfile   # combine files
cat > newfile       # create new file
cat >> file         # append to existing file
cat -n file         # number all lines
cat -b file         # number non-empty lines
cat -s file         # remove extra empty lines
```

---

<img width="1905" height="684" alt="cat" src="https://github.com/user-attachments/assets/50424467-079c-4a03-b032-59c3d19736fa" />




*Created: 2025-09-22*
