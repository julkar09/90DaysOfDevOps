# User Account Management Script

This script provides basic user account management functionalities such as creating, deleting, resetting passwords, and listing user accounts. It is designed to be run in a Unix-like environment with `bash`.

## Features

- **Create User**: Creates a new user account with a specified username and password.
- **Delete User**: Deletes an existing user account and its home directory.
- **Reset Password**: Resets the password for an existing user account.
- **List Users**: Lists all user accounts on the system.
- **Help**: Displays usage information and available options.

## Usage

### Prerequisites

- Ensure you have `sudo` privileges to execute user management commands.
- The script should be run in a `bash` shell.

### Running the Script
1. **Make the Script Executable**:
   ```bash
   chmod +x user_management.sh
   ```

2. **Run the Script**:
   ```bash
   ./user_management.sh
   ```

4. **Follow the Prompts**:
   - The script will display a menu of options.
   - Enter the corresponding option to perform the desired action.

### Options

| Option          | Description                                      |
|-----------------|--------------------------------------------------|
| `-c`, `--create`| Create a new user account.                       |
| `-d`, `--delete`| Delete an existing user account.                 |
| `-r`, `--reset` | Reset the password for an existing user account. |
| `-l`, `--list`  | List all user accounts on the system.            |
| `-h`, `--help`  | Display the help message.                        |

### Example Usage

1. **Create a User**:
   ```bash
    read -p "Enter username: " username

    if id "$username" &>/dev/null; then
        echo "User already exists! Try a different username."
    else
        read -sp "Enter password: " password
        echo
        sudo useradd -m -p $(openssl passwd -1 "$password") "$username"
   ```
   - Enter the desired username and password when prompted.

2. **Delete a User**:
   ```bash
   delete_user() {
    read -p "Enter username to delete: " username

    if id "$username" &>/dev/null; then
        sudo userdel -r "$username"
        echo "======== User deleted successfully ==========="
    else
        echo "User does not exist!"
    fi
   ```
   - Enter the username of the account you wish to delete.

3. **Reset a User's Password**:
   ```bash
   reset_password() {
    read -p "Enter username to reset password: " username

    if id "$username" &>/dev/null; then
        read -sp "Enter new password: " password
        echo
        echo -e "$password\n$password" | sudo passwd "$username" &>/dev/null
        echo "Password reset successfully!"
    else
        echo "User does not exist!"
    fi
   }
   - Enter the username and the new password when prompted.
   ```
4. **List All Users**:
   ```bash
  list_users() {
    cut -d: -f1 /etc/passwd
}
  
   
   - The script will output a list of all user accounts.

5. **Display Help**:
   ```bash
   show_help() {
    echo -e "\n\n======== CHOOSE AN OPTION ========
    -c, --create    Create a new user
    -d, --delete    Delete an existing user
    -r, --reset     Reset a user's password
    -l, --list      List all users
    -h, --help      Display this help message\n\n"
}
   - The script will display the help message with available options.

## Script Details

### Functions

1. **`create_user`**:
   - Prompts for a username and password.
   - Checks if the user already exists.
   - Creates the user with the provided credentials.

2. **`delete_user`**:
   - Prompts for a username to delete.
   - Checks if the user exists.
   - Deletes the user and their home directory.

3. **`reset_password`**:
   - Prompts for a username and new password.
   - Checks if the user exists.
   - Resets the user's password.

4. **`list_users`**:
   - Lists all user accounts by extracting usernames from `/etc/passwd`.

5. **`show_help`**:
   - Displays a help message with available options.

### Main Logic

- The script starts by displaying the help message.
- It then prompts the user to enter an option.
- Based on the selected option, the corresponding function is executed.









