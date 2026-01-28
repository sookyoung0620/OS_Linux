# 🐧 Session 8: Processes & Init Systems

## 📌 Overview

This session explains how Linux **runs, manages, and controls programs**.  
You will learn about **processes**, the **init system (systemd)**, service management, signals, and process priorities.

---

## 🎯 Learning Objectives

By the end of this session, you will be able to:

- Understand the role of the init system and what `systemd` does
- List and monitor processes using `ps`, `top`, and `htop`
- Start, stop, enable, disable, and inspect services using `systemctl`
- Understand PIDs, foreground/background jobs, and signals
- Manage processes using `kill`, `nice`, `jobs`, `&`, and `killall`

---

## 1️⃣ What is systemd?

- **systemd** is the first process started by the Linux kernel after boot
- It always has **PID 1**
- It manages the entire system lifecycle

### Responsibilities of systemd
- Managing services and daemons
- Handling logging
- Managing dependencies
- Controlling system states
- Replacing the older SysV init system with:
  - Faster boot times
  - Better logging
  - Cleaner service management

---

## 2️⃣ Unit Files

systemd uses **unit files** to define and manage system resources.

### A unit file defines:
- What to start
- How to start it
- When to start it
- Restart behavior
- Dependencies

### Common Unit Types

| Type | Description | Example |
|---|---|---|
| `.service` | Background services/daemons | `nginx.service` |
| `.timer` | Scheduled tasks (cron-like) | `backup.timer` |
| `.mount` | Mounted filesystems | `home.mount` |

---

## 3️⃣ Managing Services with `systemctl`

`systemctl` is the main command used to control systemd.

### Common Commands

| Command | Description |
|---|---|
| `systemctl status` | Show overall system status |
| `systemctl status <service>` | Show service details |
| `systemctl start <service>` | Start service immediately |
| `systemctl stop <service>` | Stop service |
| `systemctl restart <service>` | Restart service |
| `systemctl enable <service>` | Start service at boot |
| `systemctl disable <service>` | Disable autostart |
| `systemctl list-units --type=service` | List active services |

---

## 4️⃣ What is a Process?

A **process** is a running instance of a program.  
Every command you execute (even `ls`) becomes a process.

Each process has:
- PID (Process ID)
- PPID (Parent Process ID)
- State (running, sleeping, zombie, etc.)
- CPU and memory usage
- Owner (user)

---

## 5️⃣ Viewing and Managing Processes

### Common Commands

| Command | Description |
|---|---|
| `ps aux` | Show all running processes |
| `ps -f` | Full-format output |
| `top` | Real-time process monitoring |
| `htop` | Interactive process viewer |
| `kill PID` | Send signal to process |
| `kill -9 PID` | Force kill process |
| `killall name` | Kill processes by name |

Example:
```bash
ps aux | head -5
```
## 6️⃣ Understanding ps Output
| Column  | Meaning                          |
| ------- | -------------------------------- |
| USER    | Process owner                    |
| PID     | Process ID                       |
| %CPU    | CPU usage                        |
| %MEM    | Memory usage                     |
| VSZ     | Virtual memory size              |
| RSS     | Resident memory                  |
| STAT    | Process state                    |
| START   | Start time                       |
| TIME    | CPU time used                    |
| COMMAND | Command that started the process |

### Process States (STAT)

R – Running

S – Sleeping

D – Waiting for I/O

Z – Zombie

T – Stopped

+ – Foreground process

## 7️⃣ ps vs top
| Feature   | ps                   | top             |
| --------- | -------------------- | --------------- |
| View type | Snapshot             | Real-time       |
| Output    | Text output          | Interactive UI  |
| Refresh   | Manual               | Automatic       |
| Usage     | Scripting, filtering | Live monitoring |

In top:

k → kill process

P → sort by CPU

M → sort by memory

q → quit

## 8️⃣ Foreground & Background Jobs
Concepts

Foreground jobs block the terminal

Background jobs run while you continue using the terminal

Jobs are identified by job numbers (%1, %2, ...)

### Job Control Commands
| Command     | Description              |
| ----------- | ------------------------ |
| `command &` | Run in background        |
| `jobs`      | List jobs                |
| `fg %n`     | Bring job to foreground  |
| `bg %n`     | Resume job in background |
| `Ctrl+Z`    | Suspend foreground job   |
| `Ctrl+C`    | Terminate job            |
| `kill %n`   | Kill job by job number   |

9️⃣ Signals

Signals are messages sent by the OS or user to a process.

Common Signals
| Signal  | Code | Meaning              |
| ------- | ---: | -------------------- |
| SIGTERM |   15 | Graceful termination |
| SIGKILL |    9 | Force kill           |
| SIGINT  |    2 | Ctrl+C               |
| SIGSTOP |   19 | Pause process        |
| SIGCONT |   18 | Resume process       |

Sending Signals
```
kill -15 PID
kill -9 PID
kill -l
```

🔟 Process Priorities (nice)

Priority range: -20 (highest) to 19 (lowest)

Default priority: 0

Priority affects CPU scheduling

Examples
```
nice -n 10 sleep 1000 &
renice 5 <PID>
```

## 1️⃣1️⃣ Why systemd Services?
Problem with running scripts manually

Stops when terminal closes

Does not restart after reboot

Does not recover from crashes

Solution: systemd service
### Example Service File
```
[Unit]
Description=Temperature Logger

[Service]
ExecStart=/usr/local/bin/log_temp.sh
Restart=always

[Install]
WantedBy=multi-user.target
```
### Benefits
- Runs automatically at boot
- Runs in the background
- Restarts if it crashes
- Logs managed with journalctl
