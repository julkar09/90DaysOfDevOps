# Task 2: File and Directory Permissions

## Objective

1. Create a directory `/devops_workspace` and a file `project_notes.txt` inside it.
2. Set permissions so that:
   - The **owner** can read and write (edit).
   - The **group** can only read.
   - **Others** have no access.
3. Verify the permissions using `ls -l`.

---

## 1. Create the Directory and File

### 1.1 Create the Directory

Create the `devops_workspace` directory:

```bash
mkdir devops_workspace
```

### 1.2 Create the File

Create the `project_notes.txt` file inside the directory:

```bash
touch devops_workspace/project_notes.txt
```
---

## 2. Set Permissions

### 2.1 Understand Permission Notation

Linux file permissions are represented as a 3-digit octal number or a symbolic notation:

- **Owner (u)**: The user who owns the file.
- **Group (g)**: The group that owns the file.
- **Others (o)**: Everyone else.

Each permission type is represented by a number:

- **4**: Read (r)
- **2**: Write (w)
- **1**: Execute (x)

### 2.2 Set Permissions Using Octal Notation

To set the permissions as per the task:

- **Owner**: Read and Write (`6` = 4 + 2)
- **Group**: Read (`4`)
- **Others**: No access (`0`)

Run the following command:

```bash
chmod 640 devops_workspace/project_notes.txt
```

### 2.3 Verify Permissions

Use the `ls -l` command to verify the permissions:

```bash
ls -l devops_workspace/project_notes.txt
```

Output:

```bash
-rw-r----- 1 devops_user devops_team 0 Feb  4 12:22 devops_workspace/project_notes.txt
```

- `-rw-r-----`: The permissions are set as:
  - `rw-` (Owner: Read and Write)
  - `r--` (Group: Read)
  - `---` (Others: No access)
- `devops_user devops_user`: The file is owned by the `devops_user` user and `devops_user` group.

---


---

## Summary of Main Commands for this

| Task | Command |
|------|---------|
| Create Directory | `mkdir devops_workspace` |
| Create File | `touch devops_workspace/project_notes.txt` |
| Set File Permissions | `chmod 640 devops_workspace/project_notes.txt` |
| Verify File Permissions | `ls -l devops_workspace/project_notes.txt` |

---

## Final Outputs

1. **File Permissions**:

```bash
-rw-r----- 1 devops_user devops_team 0 Feb  4 12:22 devops_workspace/project_notes.txt
```

2. **Permission Tests**:
   - Owner can read and write.
   - Group can read.
   - Others cannot access.
  
---

## Terminal img
<img width="424" alt="task_2" src="https://github.com/user-attachments/assets/b0175d17-56bf-4b22-84a1-7dd25b9a35b1" />

