# `find` Command Lab Tutorial

A hands-on lab guide to practice the Linux `find` command with real examples. Perfect for learning system administration and cybersecurity skills.

---

## Lab Setup

First, let's create a test environment with various files and directories:

```bash
# Create directory structure
mkdir -p ~/find_lab/{dir1,dir2,dir3}
cd find_lab

# Create regular files
echo "Hello" > file1.txt
echo "World" > file2.log
echo "Test" > file3.tmp

# Create hidden files
touch .hidden1 .hidden2

# Create large files (5MB each)
dd if=/dev/zero of=largefile1.bin bs=1M count=5
dd if=/dev/zero of=largefile2.bin bs=1M count=5

# Create file in subdirectory
echo "Subdir file" > dir1/file3.txt

# Create symbolic link
ln -s file1.txt symlink1

# Create world-writable file
touch world.txt
chmod 777 world.txt
```

## Lab Exercises

### 1. Basic File Discovery

```bash
# List all files and directories
find .

# Expected output: Shows all files including subdirectories
```

### 2. Search by Name

```bash
# Find specific file by exact name
find . -name "file1.txt"

# Case-insensitive search for .LOG files
find . -iname "*.log"
```

### 3. Filter by File Type

```bash
# Find all directories
find . -type d

# Find all regular files
find . -type f

# Find symbolic links
find . -type l
```

### 4. Filter by Size

```bash
# Find files larger than 5MB
find . -size +5M

# Find files smaller than 1KB
find . -size -1k
```

### 5. Filter by Permissions

```bash
# Find world-writable files (security check)
find . -perm -002
```

### 6. Filter by Time

```bash
# Find files modified in the last 1 day
find . -mtime -1

# Find files accessed more than 2 days ago
find . -atime +2
```

### 7. Actions with `-exec` and `-delete`

```bash
# Count lines in all .txt files
find . -name "*.txt" -exec wc -l {} \;

# Delete all .tmp files
find . -name "*.tmp" -delete

# Copy all log files to another directory
mkdir ~/find_lab_logs
find . -name "*.log" -exec cp {} ~/find_lab_logs/ \;

# Search for files containing specific text
find . -type f -exec grep -i "password" {} \;
```

## Complete Lab Session

Here's the full sequence of commands from the lab session:

```bash
# Setup
mkdir -p ~/find_lab/{dir1,dir2,dir3}
cd find_lab

# Create test files
echo "Hello" > file1.txt
echo "World" > file2.log
echo "Test" > file3.tmp
touch .hidden1 .hidden2
dd if=/dev/zero of=largefile1.bin bs=1M count=5
dd if=/dev/zero of=largefile2.bin bs=1M count=5
echo "Subdir file" > dir1/file3.txt

# Verify setup
ls
ls -la

# Basic find operations
find .                           # List everything
find . -name "file1.txt"         # Find by exact name
find . -iname "*.log"            # Case-insensitive pattern

# Type filters
find . -type d                   # Directories only
find . -type f                   # Regular files only
ln -s file1.txt symlink1         # Create symlink
find . -type l                   # Find symlinks

# Size filters
find . -size +5M                 # Files > 5MB
find . -size -1k                 # Files < 1KB

# Permission filters
touch world.txt
chmod 777 world.txt
find . -perm -002                # World-writable files

# Time filters
find . -mtime -1                 # Modified last day
find . -atime +2                 # Accessed >2 days ago

# Actions
find . -name "*.txt" -exec wc -l {} \;           # Count lines
find . -name "*.tmp" -delete                     # Delete files
mkdir ~/find_lab_logs
find . -name "*.log" -exec cp {} ~/find_lab_logs/ \;  # Copy files
find . -type f -exec grep -i "password" {} \;   # Search content
```

## Key Learning Points

### File Types
- `d` = directory
- `f` = regular file  
- `l` = symbolic link

### Size Modifiers
- `+` = greater than
- `-` = less than
- Units: `k` (KB), `M` (MB), `G` (GB)

### Time Options
- `-mtime` = modification time
- `-atime` = access time
- `-ctime` = change time (metadata)

### Permission Notation
- `-002` = world-writable
- `-004` = world-readable
- `-4000` = setuid bit

## Security Applications

```bash
# Find SUID binaries (potential privilege escalation)
find /usr -type f -perm -4000 2>/dev/null

# Find world-writable files (security risk)
find / -type f -perm -002 2>/dev/null

# Find large files (potential data exfiltration)
find /tmp -type f -size +100M

# Find recently modified files (incident response)
find /var/log -type f -mtime -1

# Search for sensitive files
find / -name "*.key" -o -name "*.pem" 2>/dev/null
```

## Cleanup

```bash
# Remove lab directory when done
cd ~
rm -rf find_lab find_lab_logs
```

---

## Tips for Practice

1. **Start simple**: Begin with basic name searches before moving to complex filters
2. **Use 2>/dev/null**: Redirect errors when searching system directories
3. **Test before executing**: Use `-print` to verify results before using `-exec` or `-delete`
4. **Combine filters**: Use multiple criteria for precise searches
5. **Escape special characters**: Use quotes around patterns with wildcards

---




<img width="939" height="996" alt="Screenshot from 2025-09-26 01-04-10" src="https://github.com/user-attachments/assets/124cbf10-6022-4713-824c-b16fe5d6e919" />

<img width="939" height="996" alt="Screenshot from 2025-09-26 01-04-18" src="https://github.com/user-attachments/assets/59f5a061-150c-462e-a432-899cbdcaf9d9" />

<img width="939" height="996" alt="Screenshot from 2025-09-26 01-04-26" src="https://github.com/user-attachments/assets/d82d4630-59ec-406e-8b79-e13ecca8591d" />

<img width="939" height="996" alt="Screenshot from 2025-09-26 01-04-32" src="https://github.com/user-attachments/assets/a3d82d96-4ac0-41f6-908d-09092714b072" />


*Lab created: 2025-09-25*
