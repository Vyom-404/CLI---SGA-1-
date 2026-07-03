# Question 2 - Secure Project Workspace Setup

## Objective

The objective of this task is to create a secure project workspace for storing project files and documentation and to configure appropriate Linux permissions.

The task includes creating a directory structure, checking file permissions before and after modification, verifying ownership details, checking the umask value, and explaining how permissions protect project data.

---

## Command 1

```bash
cd ~/Graded_Lab_Assignment
```

### Observation

This command changed the current working directory to the main `Graded_Lab_Assignment` directory.

This ensured that the Question 2 folder was created inside the assignment repository.

---

## Command 2

```bash
mkdir -p Question2/screenshots
```

### Observation

This command created the `Question2` directory along with a `screenshots` subdirectory.

The `-p` option created the required directory structure and avoided an error if the directory already existed.

---

## Command 3

```bash
cd Question2
```

### Observation

This command changed the current working directory to the `Question2` directory.

All subsequent commands for the secure workspace setup were executed from this directory.

---

## Command 4

```bash
mkdir -p project_workspace/{documents,data,scripts}
```

### Observation

This command created the main `project_workspace` directory with three subdirectories: `documents`, `data`, and `scripts`.

Brace expansion allowed all three subdirectories to be created using a single command.

---

## Command 5

```bash
find project_workspace -type d
```

### Observation

This command displayed all directories inside `project_workspace`.

The output confirmed that the required directory structure had been created successfully.

---

## Command 6

```bash
touch project_workspace/documents/project_notes.txt
```

### Observation

This command created an empty file named `project_notes.txt` inside the `documents` directory.

The file represents project documentation stored in the secure workspace.

---

## Command 7

```bash
touch project_workspace/data/project_data.txt
```

### Observation

This command created an empty file named `project_data.txt` inside the `data` directory.

The file represents project-related data stored in the workspace.

---

## Command 8

```bash
touch project_workspace/scripts/run_project.sh
```

### Observation

This command created an empty shell script file named `run_project.sh` inside the `scripts` directory.

The file represents a project script stored in the workspace.

---

## Command 9

```bash
find project_workspace -type f
```

### Observation

This command displayed all regular files inside the project workspace.

The output confirmed that `project_data.txt`, `project_notes.txt`, and `run_project.sh` had been created successfully.

---

## Command 10

```bash
umask
```

### Observation

The `umask` command displayed the current user file-creation mask.

**Output observed:** `0002`

This value influences the default permissions assigned to newly created files and directories.

---

## Command 11

```bash
ls -l project_workspace/documents/project_notes.txt
```

### Observation

This command displayed the permissions and ownership details of `project_notes.txt` before modification.

**Permission observed before modification:** `-rw-rw-r--`

This indicated that the owner and group had read and write permissions, while other users had read-only permission.

---

## Command 12

```bash
chmod 600 project_workspace/documents/project_notes.txt
```

### Observation

This command changed the permissions of `project_notes.txt` to mode `600`.

Permission mode `600` gives read and write access only to the file owner and removes all permissions for the group and other users.

---

## Command 13

```bash
ls -l project_workspace/documents/project_notes.txt
```

### Observation

This command displayed the file permissions after modification.

**Permission observed after modification:** `-rw-------`

The output confirmed that only the file owner had read and write access.

---

## Command 14

```bash
chmod 700 project_workspace
```

### Observation

This command changed the permissions of the main `project_workspace` directory to mode `700`.

This gives the owner read, write, and execute permissions while denying all access to group members and other users.

---

## Command 15

```bash
ls -ld project_workspace
```

### Observation

This command displayed the permissions of the `project_workspace` directory itself.

**Permission observed:** `drwx------`

The output confirmed that only the directory owner could read, modify, and access the workspace.

---

## Command 16

```bash
ls -l project_workspace/documents/project_notes.txt
```

### Observation

This command displayed the current permissions and ownership information of the protected project file.

The output confirmed that the file remained restricted to the owner with permission mode `600`.

---

## Command 17

```bash
stat project_workspace/documents/project_notes.txt
```

### Observation

The `stat` command displayed detailed metadata for `project_notes.txt`.

The output showed permission mode `0600`, user ownership, group ownership, file size, inode information, and timestamps.

**Owner observed:** `vyomg20082005`

**Group observed:** `vyomg20082005`

---

## Command 18 - Generate Project Workspace Report

```bash
{
  echo "SECURE PROJECT WORKSPACE REPORT"
  echo "==============================="
  echo
  echo "1. Directory Structure Created"
  find project_workspace -type d
  echo
  echo "2. Current File Permissions After Modification"
  ls -l project_workspace/documents/project_notes.txt
  echo
  echo "3. Ownership Details"
  stat project_workspace/documents/project_notes.txt
  echo
  echo "4. Umask Value Used"
  umask
  echo
  echo "5. Explanation of Permission Protection"
  echo "The project workspace uses restrictive Linux permissions to protect project data."
  echo "Permission mode 600 allows only the file owner to read and write the protected file."
  echo "Permission mode 700 on the workspace allows only the owner to read, write, and access the directory."
  echo "These permissions reduce unauthorized access by group members and other users."
} > Project_Workspace_Report.txt
```

### Observation

This grouped command collected the workspace directory structure, modified file permissions, ownership information, umask value, and permission-protection explanation.

The `>` redirection operator created `Project_Workspace_Report.txt` and stored the generated report inside it.

---

## Command 19 - Add Before-Modification Permission to Report

```bash
sed -i '/2\. Current File Permissions After Modification/i\
2. File Permissions Before Modification\
-rw-rw-r-- 1 vyomg20082005 vyomg20082005 0 Jul 3 06:24 project_workspace/documents/project_notes.txt\
' Project_Workspace_Report.txt
```

### Observation

This command inserted the previously observed before-modification permission information into `Project_Workspace_Report.txt`.

The before-modification state was `-rw-rw-r--`, which had already been observed before applying `chmod 600`.

This ensured that the final report contained both the file permission state before modification and the state after modification.

---

## Command 20

```bash
cat Project_Workspace_Report.txt
```

### Observation

The `cat` command displayed the contents of `Project_Workspace_Report.txt` directly in the terminal.

The output verified that the report contained the directory structure, permissions before and after modification, ownership details, umask value, and explanation of permission protection.

---

## Directory Structure Created

The following secure project workspace structure was created:

```text
project_workspace/
├── data/
│   └── project_data.txt
├── documents/
│   └── project_notes.txt
└── scripts/
    └── run_project.sh
```

---

## Permission Summary

| Resource | Before Modification | After Modification | Purpose |
|---|---|---|---|
| `project_notes.txt` | `-rw-rw-r--` | `-rw-------` | Restricts file access to the owner |
| `project_workspace` | Default permissions | `drwx------` | Restricts workspace access to the owner |

---

## Ownership Details

The ownership details of `project_notes.txt` were verified using the `stat` command.

```text
Owner: vyomg20082005
Group: vyomg20082005
Permission Mode: 0600
```

The file is owned by the active user account and is protected using restrictive owner-only permissions.

---

## Umask Value

The following umask value was observed:

```text
0002
```

The umask value affects the default permissions assigned when new files and directories are created.

With a umask of `0002`, write permission is removed for other users while owner and group permissions remain available according to the base creation permissions.

---

## How Permissions Protect Project Data

Linux permissions protect project data by controlling which users can read, modify, execute, or access files and directories.

Permission mode `600` on `project_notes.txt` allows only the owner to read and write the file. Group members and other users receive no permissions on the protected file.

Permission mode `700` on `project_workspace` allows only the owner to read the directory contents, create or modify files, and enter the directory. Group members and other users are denied access.

These restrictive permissions reduce the risk of unauthorized viewing, modification, or deletion of sensitive project information.

---

## Files Included

The Question 2 directory contains the following assignment files and directories:

```text
Question2/
├── Project_Workspace_Report.txt
├── README.md
├── project_workspace/
│   ├── data/
│   │   └── project_data.txt
│   ├── documents/
│   │   └── project_notes.txt
│   └── scripts/
│       └── run_project.sh
└── screenshots/
```

The `screenshots` directory contains evidence of command execution, permissions, ownership details, and report output.

---

## Conclusion

A secure project workspace was successfully created with separate directories for documents, data, and scripts.

The file permissions of `project_notes.txt` were inspected before modification as `-rw-rw-r--` and then restricted using `chmod 600`, resulting in `-rw-------`.

The main `project_workspace` directory was protected using `chmod 700`, resulting in `drwx------`.

Ownership details were verified using the `stat` command, and the active umask value was recorded as `0002`.

The final results were documented in `Project_Workspace_Report.txt`, and screenshots were included as evidence of command execution and output.
