# Session 4: CLI Basics – Commands & Navigation


## 1. Objectives

By the end of this session, you should be able to:
- Understand what a CLI is
- Navigate the Linux filesystem
- List files and directories
- Create, move, rename, and delete files and folders
- Build basic command-line reflexes

---

## 2. What is a CLI?

### Definition
- **CLI (Command Line Interface)** is a text-based way to interact with a computer.
- Users type commands instead of clicking buttons.
- It provides more control, speed, and flexibility than graphical interfaces (GUI).

---

## 3. Advantages of the CLI

- **Remote access**
  - Uses fewer system and network resources
  - Ideal for remote servers and low-spec machines
- **Efficiency**
  - Perform actions on many files with a single command
- **Automation**
  - Commands can be combined into scripts
- **Power-user features**
  - Some operations are only possible via CLI

---

## 4. Disadvantages of the CLI

- **Error-prone**
  - A small typo can delete or move important files
- **Learning curve**
  - Commands must be learned and practiced regularly
- **Hard to undo**
  - Most commands cannot be reversed
- **Hard to remember**
  - UNIX provides hundreds of commands

---

## 5. Linux Command Structure

A typical command is composed of:
- **Prompt**
- **Command**
- **Option(s)**
- **Argument(s)**

Example:
```bash
ls -r /home/$USER
```
## 6. Linux Command Basics

- Linux commands are **case-sensitive**
  - `ls` ≠ `LS`
- Commands can have **options** and **arguments**

### Options
```bash
ls -r
ls --reverse
```
### Arguments
```bash
ls /tmp
```
### multiple commands on one line
```bash
ls; date
```
### Manual pages
```bash
man ls
```

## 7. Commands That Give Information
Common Information Commands
```bash
hostname        # Display machine name
date            # Display current date and time
date +%D        # Display date only
date +%T        # Display time only
who             # Show logged-in users
whoami          # Show current user
env             # Show environment variables
uptime          # Show how long the system has been running
uname            # Show system information
uname -r        # Kernel version
uname -n        # Network node hostname
man uname       # Manual for uname
```
## 8. Directory-Related Commands

```bash
pwd             # Show current directory
ls              # List directory contents
cd              # Change directory
mkdir            # Create a directory
rmdir            # Remove an empty directory
mv              # Move or rename files/directories

Useful ls Options
ls -l    # Long format (permissions, size, date)
ls -a    # Show hidden files
ls -t    # Sort by modification time
ls -r    # Reverse order
ls -lrt  # Detailed view, oldest first
```
## 9. File-Related Commands
```bash
cp      # Copy files
mv      # Move or rename files
rm      # Remove files
touch   # Create or update files

Useful rm Options
rm -i   # Ask before deleting
rm -r   # Recursive delete (directories)
rm -f   # Force delete (no confirmation)
```

## 10. Important Shortcuts
```bash
cd ..   # Move up one directory
cd -    # Go to previous directory
cd ~    # Go to home directory
!!      # Repeat last command
```
## 11. Pattern Matching (Wildcards)

Pattern matching allows you to select multiple files using special characters
called **wildcards**.

### Common Wildcards

| Pattern | Meaning |
|--------|--------|
| `*` | Matches any number of characters |
| `?` | Matches exactly one character |
| `[wtz]` | Matches one character: w, t, or z |
| `[a-p]` | Matches one character between a and p |

### Examples
```bash
ls *.txt          # List all files ending with .txt
ls ?.sh           # List files with exactly one character before .sh
ls [ab]*          # List files starting with a or b
ls file[1-3].txt  # List file1.txt, file2.txt, file3.txt
```

## 12. Lab Exercises
```bash
mkdir ~/lab
cd ~/lab
touch file1.txt file2.txt file3.txt notes.md data.csv
mkdir backup
cp *.txt backup/
mv file3.txt final.txt
mkdir docs
mv notes.md docs/
rm data.csv
rm -r docs
```
## 13. More Practice Labs
```bash
touch test.txt
rm test.txt

touch test1.txt test2.txt test1.csv report.md
ls test?.txt
ls *.md
ls test*.*

man cp    # Find the option to copy directories (-r)

mkdir lab
mv test1.txt test2.txt test1.csv report.md lab/
cp -r lab lab_final
```
