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

1. **Clone the Repository** (if applicable):
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Make the Script Executable**:
   ```bash
   chmod +x user_management.sh
   ```

3. **Run the Script**:
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
   ./user_management.sh -c
   ```
   - Enter the desired username and password when prompted.

2. **Delete a User**:
   ```bash
   ./user_management.sh -d
   ```
   - Enter the username of the account you wish to delete.

3. **Reset a User's Password**:
   ```bash
   ./user_management.sh -r
   ```
   - Enter the username and the new password when prompted.

4. **List All Users**:
   ```bash
   ./user_management.sh -l
   ```
   - The script will output a list of all user accounts.

5. **Display Help**:
   ```bash
   ./user_management.sh -h
   ```
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









