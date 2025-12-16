## 1. View and Inspect Running Processes
Instructions:
- Run ps aux to list all processes.
- Identify:
  - Your shell process (bash)
  - A background service (e.g. systemd, ssh)
  - Any process with high CPU usage
- Use ps -o pid,ppid,ni,stat,cmd
- Run top, sort by memory and CPU (M, then P), then quit (q).
```bash
ps aux
ps -o pid,ppid,ni,stat,cmd
top
```
## 2. Foreground and Background Jobs
Instructions:
- Run sleep 120 &
- Use jobs
- Bring it to foreground with fg %1
- Suspend with CTRL+Z
- Resume in background with bg %1
```bash
sleep 120 &
jobs
fg %1
# CTRL+Z
bg %1
```
## 3. Kill and Signals
Instructions:
- Start sleep 200 &
- Find PID using ps
- Use kill -15 <PID>
- Restart and use kill -9 <PID>
- Try killall sleep
```bash
sleep 200 &
ps aux | grep sleep
kill -15 <PID>
kill -9 <PID>
killall sleep
```
## 4. Nice and Renice
Instructions:
- Run nice -n 10 sleep 300 &
- Check nice value
- Change with renice
- Try renicing a root-owned process
```bash
nice -n 10 sleep 300 &
ps -o pid,ni,cmd
renice 5 <PID>
```
## 5. Trap Signals in a Script
Create a script that catches SIGINT.
```bash
#!/bin/bash

trap "echo SIGINT caught" SIGINT

while true
do
  echo "Running..."
  sleep 2
done
```
## 6. Create a Custom systemd Service
Create a systemd service that logs the current time.
```bash
#!/bin/bash
while true
do
  date >> /tmp/log.txt
  sleep 10
done
```
```bash
[Unit]
Description=Timer Log Service

[Service]
ExecStart=/path/to/timerlog.sh

[Install]
WantedBy=multi-user.target
```
```bash
sudo systemctl daemon-reload
sudo systemctl enable timerlog
sudo systemctl start timerlog
systemctl status timerlog
tail -f /tmp/log.txt
```
