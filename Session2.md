# Session 2: Introduction to Unix/Linux

## 1. What is an Operating System?
Linux
----
### Ubuntu
- User-friendly
- Modern
- Based on Debian
- Kubuntu is a lightweight variant

### Debian
- Focuses on stability
- Minimalist design
- Commonly used for servers

### Why Kubuntu / Ubuntu is used for this course
- Easier to install
- Lightweight

---

## 2. Linux Installation Methods

### Available Methods
- **WSL (Windows Subsystem for Linux)**  
  Run Linux directly inside Windows
- **VirtualBox**  
  Run Linux inside a virtual machine
- **Dual Boot (Mac)**  
  Native Linux installation alongside macOS

### Method Comparison

| Method | Best For | Characteristics |
|------|--------|----------------|
| WSL | Windows beginners | Easy, fast, non-destructive |
| VirtualBox | Most users | Safe, isolated environment |
| Dual Boot | Advanced users | Full performance, higher risk |


---

## 3. WSL (Windows Subsystem for Linux)

### Install a Specific Ubuntu Version
```bash
wsl --install -d Ubuntu-24.04
Check Installed Distributions and Versions
wsl -l -v
```
## 4. VirtualBox
### What is VirtualBox?
- Cross-platform virtualization software
- Runs on Windows, macOS, and Linux
- Allows multiple operating systems on one machine
- Each virtual machine runs in an isolated environment
- Limited only by disk space, memory, and CPU
### Requirements
- VirtualBox: https://www.virtualbox.org
- Ubuntu ISO: https://ubuntu.com/download
- (Optional) Xubuntu 22.04.5 LTS

### 5. Installing Linux Using V
## Installation Steps
- Download and install VirtualBox
- Launch VirtualBox → Click New
- Set: VM name/ISO image /OS type: Linux (Ubuntu/Debian)
- Configure user credentials: Username/Password/Hostname
- Allocate resources: RAM: ~50% of system memory /CPU: ~50% of available cores
- Allocate disk space: Minimum 20 GB
- Review summary → Click Finish
## Removing a Virtual Machine
- Open VirtualBox Manager
- Right-click the VM
- Select Remove
- Choose Delete all files

## 6. Mac Dual Boot (Optional)
## Why Dual Boot?
- Virtual machines use limited system resources
- Dual boot allows: Full RAM /Full CPU performance/Full disk speed /Full GPU access (important for AI, 3D, and games)
- Requirements : RAM: 4 GB / CPU: 2 GHz dual-core /Free storage: 30 GB /USB drive: 4 GB /Internet access recommended
⚠️ Always back up your system before dual booting

## 7. Playing with the Ter
### Objective
Become familiar with the command-line interface (CLI)
### Basic Commands
```bash
whoami        # Displays your username        # Shows current date and time
uname -a      # Displays system information
ls            # Lists files in the current directory
echo "Hello Linux"

Reflec
### Reflection Questionsi- What is the name of your system?-What is the name of your systemachine, or native Linux?

Which command output was the mosWhich
