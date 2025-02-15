# Task1: User & Group Management


## Objective

1. Create a user `devops_user` and add them to a group `devops_team`.
2. Set a password for `devops_user` and grant sudo access.
3. Restrict SSH login for certain users in `/etc/ssh/sshd_config`.

---

## 1. Create a User and Group

### 1.1 Create the `devops_user` User

To create a new user named `devops_user`, use the following command:

```bash
sudo useradd -m devops_user
```

- `-m`: Creates the user's home directory.


### 1.2 Create the `devops_team` Group

To create a new group named `devops_team`, use the following command:

```bash
sudo groupadd devops_team
```

### 1.3 Add `devops_user` to `devops_team`

To add the user `devops_user` to the group `devops_team`, use the following command:

```bash
sudo usermod -aG devops_team devops_user

# OR
sudo gpasswd -a devops_user devops_team
```


---

## 2. Set a Password and Grant Sudo Access

### 2.1 Set a Password for `devops_user`

If you didn't set a password during user creation, you can set it using:

```bash
sudo passwd devops_user
```

You will be prompted to enter and confirm the new password.

### 2.2 Grant Sudo Access to `devops_user`

To grant `devops_user` sudo access, add them to the `sudo` group:

```bash
sudo usermod -aG sudo devops_user
```
---

## 3. Restrict SSH Login for Certain Users

### 3.1 Edit the SSH Configuration File

Open the SSH configuration file `/etc/ssh/sshd_config` in a text editor:

```bash
sudo nano /etc/ssh/sshd_config
```


### 3.2 Restrict SSH Access


```bash
DenyUsers devops_user
```

This denies SSH access to devops_user while allowing all other users.


### 3.3 Restart the SSH Service

After making changes, restart the SSH service to apply the new configuration:

```bash
sudo systemctl restart sshd
```

### 3.4 Verify SSH Access

Attempt to log in via SSH as a user not listed in `AllowUsers`. The login should be denied. Then, log in as `devops_user` to confirm access.


#### Find the Server's or local IP Address

To connect to the SSH server, you need its IP address. Use the following command to find it:

```bash
ip a
```

Look for the inet address under your network interface (e.g., eth0 or wlp2s0). For example:

```bash
inet 172.31.5.179/24
```

#### Authenticate using SSH

On another machine (or the same machine if you're testing locally), use the ssh command to connect:

```bash
ssh devops_user@172.31.5.179
```

- Replace 172.31.5.179 with the IP address of your SSH server (or local device).

You will be prompted to enter the password for ssh_user. Enter the password you set previously.
Example Output:

```bash
devops_user@172.31.5.179's password:
Welcome to Ubuntu 22.04 LTS (GNU/Linux 5.15.0-83-generic x86_64)
...

devops_user@hostname:~$
```

---

## Final Results

1. **User and Group Creation**:
   - User `devops_user` created.
   - Group `devops_team` created.
   - `devops_user` added to `devops_team`.

2. **Password and Sudo Access**:
   - Password set for `devops_user`.
   - `devops_user` granted sudo access.

3. **SSH Restriction**:
   - SSH access restricted to `devops_user` (or specified users).
   - SSH service restarted and verified.

---

## Files Modified

- `/etc/passwd`: Contains user information.
- `/etc/group`: Contains group information.
- `/etc/ssh/sshd_config`: SSH configuration file.

---

## Terminal img
<img width="423" alt="task_1" src="https://github.com/user-attachments/assets/06446283-c05e-4b9e-9a72-e54234e25677" />


