# `ls` — GitHub Cheat Sheet

A concise, GitHub-friendly Markdown guide for the Linux `ls` command. Use this in repos, study notes, or CTF/infosec cheat sheets.

---

## Quick summary

`ls` lists directory contents. Syntax:

```bash
ls [OPTIONS] [PATH...]
```

By default it prints file and directory names. Combine options to get long listings, hidden files, sorting, and more.

---

## Common options (top picks)

| Option         |                                       Meaning | Example           |
| -------------- | --------------------------------------------: | ----------------- |
| `-l`           | Long listing (permissions, owner, size, date) | `ls -l`           |
| `-a`           |   Show all files (including hidden `.` files) | `ls -a`           |
| `-h`           |              Human-readable sizes (with `-l`) | `ls -lh`          |
| `-t`           |      Sort by modification time (newest first) | `ls -lt`          |
| `-S`           |                  Sort by size (largest first) | `ls -lS`          |
| `-R`           |               Recursive (list subdirectories) | `ls -R /var/www`  |
| `-r`           |         Reverse order (useful with `-t`/`-S`) | `ls -ltr`         |
| `--color=auto` |   Colorize output (many distros default this) | `ls --color=auto` |

---

## Useful combos 

```bash
# Detailed + hidden + human sizes
ls -alh

# Detailed, sorted by time, newest first
ls -lhlt

# Detailed, largest first
ls -lSh

# Show only directories
ls -d */

# Show files matching a pattern (e.g., .sh)
ls -la *.sh

# Recursive listing (careful — can be huge)
ls -R /path/to/dir
```

---
<img width="1255" height="491" alt="ls-lh" src="https://github.com/user-attachments/assets/1713d14c-c473-4d47-92b1-0b4ade4dd6a1" />

<img width="1920" height="110" alt="Screenshot from 2025-09-22 21-29-48" src="https://github.com/user-attachments/assets/29aa5afe-afec-4c04-8306-04994729b086" />


## Reading `ls -l` output

Example:

```
-rw-r--r-- 1 savindu-ak staff 1.2K 2025-09-22 20:00 notes.txt
```

* `-rw-r--r--` → type and permissions (`d` = dir, `l` = link, `c` = char dev, `b` = block dev, `p` = fifo, `s` = socket)
* `1` → hard links
* `savindu-ak` → owner
* `staff` → group
* `1.2K` → size (human-readable)
* `2025-09-22 20:00` → last modification time
* `notes.txt` → filename

---

## File type characters (first column of `ls -l`)

* `-` : regular file
* `d` : directory
* `l` : symbolic link
* `c` : character device (e.g., `/dev/tty1`)
* `b` : block device (e.g., `/dev/sda`)
* `p` : named pipe (FIFO)
* `s` : socket

---

## Special permission bits

* `s` in user exec position → setuid (runs as file owner)
* `s` in group exec position → setgid (process inherits group)
* `t` in others exec position → sticky bit (only owner can delete own files in dir)

Examples shown by `ls -l`:

```
-rwsr-xr-x 1 root root 40K /usr/bin/someprog  # setuid
-rwxr-sr-x 1 root staff 12K /usr/bin/sgroup   # setgid
drwxrwxrwt 10 root root 4.0K /tmp             # sticky bit
```

---
<img width="928" height="462" alt="ls-l" src="https://github.com/user-attachments/assets/b9eb35a5-13e5-45b7-a565-d9aeb7c32793" />

## `ls` in cybersecurity / CTFs (practical tips)

* `ls -la` — always run this first to reveal hidden files (`.ssh`, `.bash_history`, `.config`).
* `ls -lhlt | head` — find recently modified files (helpful to locate dropped backdoors).
* `ls -lSh` — find large suspicious files (malware, exfiltrated data).
* Check world-readable sensitive files: `ls -l /etc/passwd /etc/shadow` (if `/etc/shadow` is readable, that’s a serious misconfig).
* Inspect common hiding grounds: `/tmp`, `/dev/shm`, `/var/tmp`, web roots (`/var/www`, `/srv/http`).
* Combine with `grep` to filter results: `ls -la | grep -i key` or `ls -la | grep -E "\.pem|\.key|id_rsa"`

---

## Tips & tricks

* Use aliases in your shell (`~/.bashrc` or `~/.zshrc`):

```bash
# common alias
alias ll='ls -alh'
```

* `ls -d */` lists only directories in the current dir.
* To show inode numbers (useful for forensic linking):

```bash
ls -li
```

---

## Alternatives & related tools

* `tree` — visual directory tree (not installed by default on some distros)
* `find` — powerful search with filters (recommended for SUID/SGID discovery):

```bash
# find SUID files
find / -perm -4000 -type f 2>/dev/null
```

* `stat` — detailed single-file metadata

---

## Quick reference (cheat sheet block)

```
ls -l      # long listing
ls -a      # include hidden files
ls -h      # human sizes (with -l)
ls -S      # sort by size
ls -t      # sort by time
ls -r      # reverse order
ls -R      # recursive
ls -d */   # list directories only
```

---

## License

This cheat sheet is free to use and modify . If you remix it, a star ⭐ on the repo is appreciated but not required.

---

*Created: 2025-09-22*
