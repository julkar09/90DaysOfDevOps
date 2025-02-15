# Process Management & Monitoring

## Overview
This guide provides step-by-step instructions to start a background process, monitor it using various Linux utilities, and then terminate the process while verifying its termination.

---

## Prerequisites
- A Linux-based system (Ubuntu, CentOS, etc.)
- Basic knowledge of Linux commands
- `htop` installed (optional, but recommended)

---

## Steps to Follow

### 1. Start a Background Process
To start the background process that pings `google.com` and logs the output, run:
```bash
ping google.com > ping_test.log &
```
**Explanation:**
- `ping google.com`: Pings `google.com` continuously.
- `> ping_test.log`: Redirects the output to `ping_test.log`.
- `&`: Runs the process in the background.

---

### 2. Monitor the Process Using `ps`
The `ps` command lists running processes. To find the background process:
```bash
ps aux | grep ping
```
This will display details of the `ping` process, including its **Process ID (PID)**.

Example output:
```
user     12345  0.0  0.0  1234  456 ? Ss   10:10   0:00 ping google.com
```
Here:
- `12345` is the PID of the `ping` process.

---

### 3. Monitor the Process Using `top`
The `top` command provides real-time system monitoring, including running processes. Run:
```bash
top
```
- Look for `ping` in the list.
- Press `q` to exit.

---

### 4. Monitor the Process Using `htop`
If `htop` is installed, you can use it for better visualization:
```bash
htop
```
- Scroll to find `ping` or press `F3` and search for `ping`.
- Press `q` to exit.

---

### 5. Kill the Process
#### Using `kill`
First, find the PID using `ps aux | grep ping`, then terminate it:
```bash
kill 12345
```
Replace `12345` with the actual PID.

#### Using `killall`
To kill all `ping` processes:
```bash
killall ping
```

---

### 6. Verify the Process is Gone
Check if the process is still running:
```bash
ps aux | grep ping
```
If no output is returned, the process has been successfully terminated.

Alternatively, verify using `top` or `htop`:
```bash
top
```
```bash
htop
```
If `ping` is not listed, it is no longer running.

---

## Summary of Commands
| Step | Command |
|------|---------|
| Start background process | `ping google.com > ping_test.log &` |
| Monitor using `ps` | `ps aux | grep ping` |
| Monitor using `top` | `top` |
| Monitor using `htop` | `htop` |
| Kill process by PID | `kill <PID>` |
| Kill all `ping` processes | `killall ping` |
| Verify process termination | `ps aux | grep ping` |

---
## Terminal img

<img width="633" alt="task_5 1" src="https://github.com/user-attachments/assets/716813bd-7288-43e3-b2ae-fbd1e8cc8712" />

<img width="916" alt="taak_5 2" src="https://github.com/user-attachments/assets/5422730b-6653-492b-920f-110993a93843" />






