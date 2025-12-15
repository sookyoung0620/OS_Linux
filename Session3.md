# Session 3: Linux Architecture & File Systems

## 1. Objectives

- Identify core Linux system components (hardware, kernel, shell, userland)
- Understand the Linux boot process
- Explore Linux file systems and directory structure
- Practice filesystem navigation and observation

---

## 2. Linux System Architecture

### System Components
- **Hardware**
  - Physical components: CPU, memory, disk, devices
- **Kernel**
  - Core of the operating system
  - Manages hardware, memory, CPU, processes, and I/O
  - Runs in its own protected memory space (kernel space)
- **Shell**
  - User interface to interact with the kernel
  - Interprets and executes commands
- **User Applications**
  - Browsers, editors, games, services
  - Run on top of the shell and kernel

---

## 3. Kernel: Core of Linux

- Acts as the bridge between software and hardware
- Modular system of drivers
- Manages:
  - Memory allocation
  - CPU scheduling
  - File I/O
- Operates in **kernel space**, separate from user space

---

## 4. Shell: User Interface

- Started automatically when a user logs in
- Provides an environment to run commands and scripts
- Defines command syntax and scripting rules
- Default shell used in this course: **bash**
  - BASH = *Bourne Again SHell*

### Shell Inspection Commands
```bash
echo $SHELL    # Shows default shell
echo $0        # Shows current shell
chsh --list-shells
```
## Shell Customization

- Shell startup scripts configure the user environment
- For **bash**, customization is done in `~/.bashrc`

### Examples
```bash
alias ls='ls -rtl'
PATH=$PATH:/data/myusername
EDITOR=/usr/bin/vim
```
## 5. Different Linux Shells

- **sh** – Original Bourne shell
- **bash** – Extended replacement for sh
- **csh** – C language–style shell
- **tcsh** – Enhanced version of csh
- **ksh** – Korn shell (sh-compatible)
- **zsh** – Extended sh with advanced features
- **dash** – Lightweight shell used in Debian

---

## 6. Applications and Services

### Applications
- Browsers
- Text editors
- Games

### Services
- Web servers
- Mail servers
- Background daemons

📌 Everything runs on top of the **shell** and **kernel**

---

## 7. Linux Boot Process

### Basic Boot Steps
1. BIOS / UEFI initializes hardware
2. Bootloader (MBR → GRUB) is loaded
3. Kernel is loaded and initialized
4. Init system (systemd) starts services and login

---

## 8. BIOS / UEFI Initialization

- Performs Power-On Self-Test (POST)
- Checks essential hardware:
  - CPU
  - RAM
  - Storage devices
- Searches storage for a bootable device
- Loads the bootloader from the MBR

---

## 9. MBR (Master Boot Record)

- First **512 bytes** of a bootable disk
- Contains a small program to load the full bootloader
- Typically located on:
  - `/dev/sda`
  - `/dev/hda`

---

## 10. GRUB (GRand Unified Bootloader)

- Most common Linux bootloader
- Displays a menu to select kernels or OS options

### Configuration Files
- `/boot/grub/grub.conf`
- `/etc/grub.conf`

---

## 11. Kernel Initialization

- Kernel takes full control of the system
- Executes `/sbin/init` (PID = 1)
- Sets up a temporary root filesystem using **initrd**
- Loads essential drivers before mounting the real filesystem

---

## 12. Init / systemd

- First user-space process (PID = 1)
- Brings the system to a usable state

### Responsibilities
- Start services (sshd, cron, networking)
- Mount filesystems (`/home`, `/var`)
- Initialize logging (journald, rsyslog)
- Configure networking
- Start login managers (getty, GDM)

---

## 13. Runlevels and systemd Targets

### Traditional Runlevels
- **0**: Halt
- **1**: Single-user (rescue)
- **3**: Multi-user (no GUI)
- **5**: Multi-user (GUI)
- **6**: Reboot

### systemd Targets
- `poweroff.target`
- `rescue.target`
- `multi-user.target`
- `graphical.target`
- `reboot.target`
- `emergency.target`

---

## 14. Linux File System

### What is a File System?
- Organizes data on disk
- Stores files and directories
- Defines access permissions

### Popular File Systems
- **FAT** – Old MS-DOS / early Windows
- **NTFS** – Modern Windows
- **ext2 / ext3 / ext4** – Linux
- **HFS+** – Older macOS
- **APFS** – Modern macOS / iOS

---

## 15. Files in Linux

### Types of Files
- **Regular files (-)**: text, data, programs
- **Directories (d)**: containers for files
- **Devices**: hardware represented as files (`/dev`)
- **Links (l)**:
  - Hard links
  - Symbolic (soft) links

📌 **Everything in Linux is a file**

### File Naming Rules
- Case-sensitive (`File.txt` ≠ `file.txt`)
- Avoid special characters: `/ * ? : $ %`

---

## 16. Directory Structure

- Linux uses a hierarchical tree structure
- Root directory: `/`

### Important Directories
- `/bin` – Essential user commands (ls, cp, cat)
- `/boot` – Bootloader files, kernels, initrd
- `/dev` – Device files (disks, terminals)
- `/etc` – System-wide configuration files
- `/home` – User home directories
- `/lib` – System libraries and kernel modules
- `/media` – Auto-mounted devices (USB, CD)
- `/mnt` – Temporary mount points
- `/opt` – Optional third-party software
- `/root` – Home directory for root user
- `/sbin` – System administration binaries
- `/srv` – Data served by system services
- `/tmp` – Temporary files
- `/usr` – User applications and shared resources
- `/usr/bin` – Most user command binaries

---

## 17. Paths

### What is a Path?
- Unique location of a file or directory
- Uses `/` to describe hierarchy

### Types of Paths

#### Absolute Path
```text
/home/base/myData/test.config
```
---
## 18. Basic Navigation Commands
```bash
pwd   # Show current directory
ls    # List files and directories
cd    # Change directory
```
## 19. Exploration Tasks

### Explore Important Directories
```bash
ls /bin        # Essential system commands
ls /usr/bin    # Most user applications
ls /sbin       # System administration binaries
ls /tmp        # Temporary files
ls /boot       # Bootloader and kernel files
```
### Check Permissions of a System File
ls -l /etc/passwd   # View file permissions and ownership

### Inspect Device Files
```bash
ls /dev        # List device files
```

### Shell and Process Information
```bash
echo $SHELL    # Show default shell
echo $0        # Show current shell
ps -p $$       # Show current shell process info
tty            # Show current terminal device
who am i       # Show logged-in user and terminal
```

### Check Mounted Disks
```bash
lsblk          # List block devices and partitions
df -h          # Show disk usage and mounted filesystems
```

### Inspect Boot Files
```bash
ls /boot       # List kernel and bootloader files
cat /etc/fstab # Show filesystem mount configuration
```

### View systemd Targets
```bash
systemctl list-units --type=target   # List active systemd targets
```
