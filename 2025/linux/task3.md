# Task 3: Log File Analysis with AWK, Grep, and Sed

## Objective

1. Download the `Linux_2k.log` file from the LogHub GitHub repository.
2. Extract insights using the following commands:
   - Use `grep` to find all occurrences of the word "error".
   - Use `awk` to extract timestamps and log levels.
   - Use `sed` to replace all IP addresses with `[REDACTED]` for security.
3. Bonus: Find the most frequent log entry using `awk` or `sort | uniq -c | sort -nr | head -10`.


## Step 1: Download the Log File

### 1.1 Clone the LogHub Repository

Clone the LogHub repository to your local machine:

```bash
wget https://github.com/logpai/loghub.git
```
## Step 2: Analyze the Log File

### 2.1 Use `grep` to Find All Occurrences of "error"

Search for all lines containing the word "error" (case-insensitive):

```bash
grep -i "error" Linux_2k.log
```

- `-i`: Makes the search case-insensitive.

#### No Output

No keyword matches "error"


### 2.2 Use `awk` to Extract Timestamps and Log Levels

Extract the timestamp (first field) and log level (second field) from each log entry:

```bash
awk '{print $1, $2, $3, $6, $7}' Linux_2k.log | tail -n 10
  
```

- `$1`: Represents the first field (month).
- `$2`: Represents the second field (date).
- `$3`: Represents the third field (timestamp).
- `$6`: Represents the log levels.
- `$7`: Represents the log levels.

#### Output

```bash
Jul 27 14:41:59 combo kernel: VFS: Disk 
Jul 27 14:41:59 combo kernel: Dquot-cache hash 
Jul 27 14:41:59 combo kernel: SELinux:  Registering 
Jul 27 14:41:59 combo kernel: Initializing Cryptographic 
Jul 27 14:41:59 combo kernel: pci_hotplug: PCI 
Jul 27 14:42:00 combo kernel: isapnp: Scanning 
Jul 27 14:42:00 combo kernel: isapnp: No 
Jul 27 14:42:00 combo kernel: Real Time 
Jul 27 14:42:00 combo kernel: Linux agpgart 
...
...
```


### 2.3 Use `sed` to Replace IP Addresses with `[REDACTED]`

Replace all IP addresses in the log file with `[REDACTED]`:

```bash
sed -E 's/([0-9]{1,3}\.){3}[0-9]{1,3}/[REDACTED]/g' Linux_2k.log | tail -n 10
```

- `-E`: Enables extended regular expressions.
- `([0-9]{1,3}\.){3}[0-9]{1,3}`: Matches an IP address (e.g., `172.31.5.179`).
- `[REDACTED]`: Replaces the matched IP address.

#### Ouput

```bash
...
Jun 17 07:07:00 combo ftpd[29504]: connection from [REDACTED] (24-54-76-216.bflony.adelphia.net) at Fri Jun 17 07:07:00 2005
Jun 17 07:07:00 combo ftpd[29508]: connection from [REDACTED] (24-54-76-216.bflony.adelphia.net) at Fri Jun 17 07:07:00 2005
Jun 17 07:07:00 combo ftpd[29507]: connection from [REDACTED] (24-54-76-216.bflony.adelphia.net) at Fri Jun 17 07:07:00 2005
Jun 17 07:07:00 combo ftpd[29505]: connection from [REDACTED] (24-54-76-216.bflony.adelphia.net) at Fri Jun 17 07:07:00 2005
Jun 17 07:07:00 combo ftpd[29506]: connection from [REDACTED] (24-54-76-216.bflony.adelphia.net) at Fri Jun 17 07:07:00 2005
Jun 17 07:07:00 combo ftpd[29509]: connection from [REDACTED] (24-54-76-216.bflony.adelphia.net) at Fri Jun 17 07:07:00 2005
Jun 17 07:07:02 combo ftpd[29510]: connection from [REDACTED] (24-54-76-216.bflony.adelphia.net) at Fri Jun 17 07:07:02 2005
Jun 17 07:07:04 combo ftpd[29511]: connection from [REDACTED] (24-54-76-216.bflony.adelphia.net) at Fri Jun 17 07:07:04 2005
Jun 17 19:43:13 combo sshd(pam_unix)[30565]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=[REDACTED]  user=guest
...
...
```

---

## Step 3: Bonus - Find the Most Frequent Log Entry

### 3.1 Use `awk` to Extract Log Messages

Extract the log messages (all fields except the first two):

```bash
awk '{for (i=5; i<=NF; i++) printf $i " "; print ""}' Linux_2k.log
```

- `NF`: Represents the number of fields in the current line.
- `for (i=5; i<=NF; i++)`: Loops through fields starting from the 5th field.

### 3.2 Find the Most Frequent Log Entry

Use `sort`, `uniq`, and `head` to find the top 10 most frequent log entries:

```bash
awk '{for (i=5; i<=NF; i++) printf $i ""; print ""}' Linux_2k.log | sort | uniq -c | sort -nr | head -n 5

```

- `sort`: Sorts the log entries alphabetically.
- `uniq -c`: Counts the occurrences of each unique log entry.
- `sort -nr`: Sorts the counts in descending order.
- `head -n 5`: Displays the top 10 most frequent log entries.

#### Output

```bash
     43 logrotate:ALERTexitedabnormallywith[1]
     16 named[2306]:notifyquestionsectioncontainsnoSOA
      7 syslogd1.4.1:restart.
      6 cups:cupsdstartupsucceeded
      6 cups:cupsdshutdownsucceeded

```

---

## Summary of Commands

| Task | Command |
|------|---------|
| Find "error" occurrences | `grep -i "error" Linux_2k.log` |
| Extract timestamps and log levels | awk '{print $1, $2, $3, $6, $7}' Linux_2k.log | tail -n 10 |
| Replace IP addresses | `sed -E 's/([0-9]{1,3}\.){3}[0-9]{1,3}/[REDACTED]/g' Linux_2k.log` |
| Find most frequent log entry | `awk '{for (i=5; i<=NF; i++) printf $i " "; print ""}' Linux_2k.log \| sort \| uniq -c \| sort -nr \| head -n 5` |

---
## Terminal img

<img width="932" alt="task_3 1" src="https://github.com/user-attachments/assets/cc285f54-c93f-40a3-ac4a-8a0d42a6ccb8" />

<img width="731" alt="task_3 2" src="https://github.com/user-attachments/assets/ab44eb53-1350-4763-a31b-28f29ae541bc" />



