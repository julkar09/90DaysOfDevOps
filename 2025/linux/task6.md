# Automate Backups with Shell Scripting

## Objectives
1. Write a shell script to back up /devops_workspace as backup_$(date +%F).tar.gz.
2. Save it in /backups and schedule it using cron.
3. Make the script display a success message in green text using echo -e.
## Features
- Automates the backup process.
- Compresses the backup using `tar`.
- Saves the backup in the `/backups` directory.
- Displays success messages in green text.
- Scheduled execution using cron.

## Prerequisites
Ensure that:
- You have a Linux-based system with shell scripting support.
- You have `tar` installed.
- You have necessary permissions to create backups in `/backups`.

## Installation and Usage

### 1. Create the Shell Script
Create a new shell script file using:
```sh
vim /home/user/backup_script.sh
```

### 2. Write the Shell Script
Add the following code:
```sh
#!/bin/bash

# Define backup variables
SOURCE_DIR="/devops_workspace"
BACKUP_DIR="/backups"
BACKUP_FILE="backup_$(date +%F).tar.gz"

# Ensure backup directory exists
mkdir -p $BACKUP_DIR

# Create backup
 tar -czf $BACKUP_DIR/$BACKUP_FILE $SOURCE_DIR

# Check if the backup was successful
if [ $? -eq 0 ]; then
    echo -e "\e[32mBackup successful: $BACKUP_DIR/$BACKUP_FILE\e[0m"
else
    echo -e "\e[31mBackup failed\e[0m"
fi
```

### 3. Make the Script Executable
Run the following command to make the script executable:
```sh
chmod +x /home/user/backup_script.sh
```

### 4. Test the Script
Execute the script manually to ensure it works correctly:
```sh
/home/user/backup_script.sh
```
You should see a success message in green if the backup is successful.

### 5. Schedule the Script with Cron
To automate the backup process, schedule it to run daily at 2 AM:
1. Open the cron table:
   ```sh
   crontab -e
   ```
2. Add the following line at the end:
   ```sh
   0 0 * * * /home/user/backup_script.sh
   ```
3. Save and exit.

## Summary of Commands
```sh
vim /home/user/backup_script.sh      # Create the shell script
chmod +x /home/user/backup_script.sh # Make it executable
/home/user/backup_script.sh          # Run it manually
crontab -e                           # Schedule it with cron
```
## Terminal img
![WhatsApp Image 2025-02-15 at 21 47 54_6ec571a2](https://github.com/user-attachments/assets/2a165128-a949-4a03-a190-bc73ed06baf9)

<img width="404" alt="task_6 1" src="https://github.com/user-attachments/assets/3f796c62-fd8a-4318-99eb-ec439bbd0e50" />




