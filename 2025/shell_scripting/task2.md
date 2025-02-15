#!/bin/bash

# Function to display usage instructions
function display_usage {
    echo "Usage: $0 <source_directory> <backup_directory>"
    echo "Example: $0 /home/user/documents /backups"
}

# Validate command-line arguments
if [ $# -ne 2 ]; then
    display_usage
    exit 1
fi

# Assign source and backup directories
SOURCE_DIR=$1
BACKUP_DIR=$2

# Create backup directory if it doesn't exist
mkdir -p "$BACKUP_DIR"

# Generate a timestamp for the backup
TIMESTAMP=$(date '+%Y-%m-%d_%H-%M-%S')
BACKUP_FILE="$BACKUP_DIR/backup_$TIMESTAMP.zip"

# Function to create a backup
function create_backup {
    echo "Creating backup of $SOURCE_DIR..."
    zip -r "$BACKUP_FILE" "$SOURCE_DIR" > /dev/null
    if [ $? -eq 0 ]; then
        echo "Backup created successfully: $BACKUP_FILE"
    else
        echo "Error: Backup failed."
        exit 1
    fi
}

# Function to rotate backups (keep only the last 3)
function rotate_backups {
    echo "Rotating backups to retain only the last 3..."
    BACKUPS=($(ls -t "$BACKUP_DIR"/backup_*.zip 2> /dev/null))
    if [ "${#BACKUPS[@]}" -gt 3 ]; then
        echo "Removing older backups..."
        for BACKUP in "${BACKUPS[@]:3}"; do
            rm -f "$BACKUP"
            echo "Deleted: $BACKUP"
        done
    else
        echo "No backups to rotate."
    fi
}

# Execute backup and rotation
create_backup
rotate_backups

echo "Backup process completed."
