# Linux CLI Graded Lab Assignment

## Overview

This repository contains the complete solutions and documentation for the Linux Command Line Interface graded lab assignment.

The assignment was completed using Google Cloud Shell and covers Linux environment verification, file permissions, file system links, file I/O operations, and storage health assessment.

Each question is organized into a separate directory containing the required report files, screenshots of command execution and outputs, technical observations, and question-specific documentation.

---

## Repository Structure

```text
Graded_Lab_Assignment/
├── Question1/
├── Question2/
├── Question3/
├── Question4/
├── Question5/
└── README.md
```

---

## Question 1 - Linux Environment Verification

This question focuses on verifying the Linux environment and collecting basic system information.

### Tasks Performed

- Displayed the current username
- Displayed groups associated with the user account
- Identified the current shell
- Displayed the current working directory
- Listed files and directories in the workspace
- Verified network connectivity
- Generated an environment verification report

### Main Report

```text
Question1/Environment_Report.txt
```

### Documentation

See the detailed Question 1 documentation inside:

```text
Question1/README.md
```

---

## Question 2 - Secure Project Workspace Setup

This question focuses on creating a secure project workspace and configuring Linux file and directory permissions.

### Tasks Performed

- Created a project directory structure
- Created sample project files
- Checked file permissions before modification
- Modified file permissions using `chmod`
- Restricted access to the project workspace
- Verified ownership information
- Observed the active `umask` value
- Documented how Linux permissions protect project data

### Main Report

```text
Question2/Project_Workspace_Report.txt
```

### Documentation

See the detailed Question 2 documentation inside:

```text
Question2/README.md
```

---

## Question 3 - File System and Link Analysis

This question focuses on investigating hard links and symbolic links in Linux.

### Tasks Performed

- Created an original file
- Created a hard link
- Created a symbolic link
- Compared inode numbers
- Collected file metadata using Linux utilities
- Deleted the original file
- Tested hard link behavior after deletion
- Tested symbolic link behavior after deletion
- Documented conclusions from the experiment

### Main Report

```text
Question3/Link_Analysis_Report.txt
```

### Documentation

See the detailed Question 3 documentation inside:

```text
Question3/README.md
```

---

## Question 4 - File Access and I/O Investigation

This question focuses on investigating Linux file access and input/output operations.

### Tasks Performed

- Investigated open file descriptors
- Observed file descriptor information through the `/proc` filesystem
- Tested standard output redirection
- Tested standard error redirection
- Tested combined output and error redirection
- Observed shell resource limits
- Documented how Linux manages file I/O

### Main Report

```text
Question4/IO_Investigation_Report.txt
```

### Documentation

See the detailed Question 4 documentation inside:

```text
Question4/README.md
```

---

## Question 5 - Storage Health Assessment and Documentation

This question focuses on assessing Linux storage resources before application server deployment.

### Tasks Performed

- Identified available storage devices
- Inspected mounted file systems
- Collected disk usage statistics
- Examined inode utilization
- Documented storage health observations
- Provided recommendations for improving storage utilization
- Created the required report using the `vi` editor

### Main Report

```text
Question5/Storage_Assessment_Report.txt
```

### Documentation

See the detailed Question 5 documentation inside:

```text
Question5/README.md
```

---

## Tools and Environment

The assignment was completed using:

- Google Cloud Shell
- Bash shell
- Standard Linux command-line utilities
- Git
- GitHub
- `vi` editor
- `nano` editor for documentation

---

## Key Linux Commands Used

Commands used throughout the assignment include:

```bash
whoami
groups
echo
pwd
ls
ping
find
touch
chmod
umask
stat
ln
rm
cat
df
lsblk
findmnt
ulimit
vi
```

Additional Linux features investigated include:

- File permissions
- Directory permissions
- User and group ownership
- Hard links
- Symbolic links
- Inode numbers
- File descriptors
- Standard input
- Standard output
- Standard error
- Output redirection
- Error redirection
- Resource limits
- Disk utilization
- Inode utilization

---

## Reports Generated

The following main report files were created during the assignment:

```text
Question1/Environment_Report.txt
Question2/Project_Workspace_Report.txt
Question3/Link_Analysis_Report.txt
Question4/IO_Investigation_Report.txt
Question5/Storage_Assessment_Report.txt
```

---

## Screenshot Evidence

Each question directory contains a `screenshots` folder.

```text
Question1/screenshots/
Question2/screenshots/
Question3/screenshots/
Question4/screenshots/
Question5/screenshots/
```

These screenshots provide evidence of command execution, terminal outputs, report verification, and editor operations where required.

---

## Assignment Summary

This assignment provided practical experience with essential Linux command-line operations.

The exercises demonstrated how to inspect a Linux environment, manage file permissions, investigate hard and symbolic links, analyze file I/O behavior, work with file descriptors and redirection, inspect resource limits, and assess storage utilization.

All required reports, technical observations, command outputs, and screenshots are organized in their respective question directories.


## Conclusion

All five questions of the Linux CLI graded lab assignment were completed and documented.

The repository contains question-specific reports, technical observations, command execution evidence, screenshots, and detailed documentation for each task.
