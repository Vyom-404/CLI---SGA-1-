# Question 1 - Linux Environment Verification

## Objective

The objective of this task is to verify the Linux environment by checking the current user account, associated groups, current shell, working directory, workspace contents, and network connectivity.

---

## 1. Display Username

### Command

```bash
whoami
```

### Observation

The `whoami` command displays the username of the currently logged-in user.

**Output observed:** `vyomg20082005`

This confirmed the active user account in the Google Cloud Shell environment.

---

## 2. Display Groups Associated with the Account

### Command

```bash
groups
```

### Observation

The `groups` command displays the groups associated with the current user account.

This helped identify the Linux groups to which the active user belongs.

---

## 3. Identify the Current Shell

### Command

```bash
echo $SHELL
```

### Observation

The `echo $SHELL` command displays the default shell configured for the current user account.

This helped identify the shell environment being used in Google Cloud Shell.

---

## 4. Display Current Working Directory

### Command

```bash
pwd
```

### Observation

The `pwd` command displays the absolute path of the current working directory.

This confirmed the exact directory location from which the lab commands were executed.

---

## 5. List Files and Directories in the Workspace

### Command

```bash
ls -la
```

### Observation

The `ls -la` command lists all files and directories in the current workspace, including hidden files.

It also displays additional information such as:

- File permissions
- Number of links
- File owner
- Group owner
- File size
- Last modification time

This helped inspect the contents and structure of the current workspace.

---

## 6. Verify Network Connectivity

### Command

```bash
ping -c 4 google.com
```

### Observation

The `ping` command tests network connectivity with `google.com`.

The `-c 4` option limits the command to four network packets.

Successful responses confirm that the Linux environment has working network connectivity.

---

## 7. Generate Environment Report

The required Linux environment information was collected and stored in the following file:

```text
Environment_Report.txt
```

The report contains information about:

- Current username
- Associated groups
- Current shell
- Current working directory
- Files and directories in the workspace
- Network connectivity

### Command Used to View the Report

```bash
cat Environment_Report.txt
```

### Observation

The `cat` command displays the contents of `Environment_Report.txt` directly in the terminal.

This was used to verify that the required Linux environment information had been successfully recorded in the report file.

---

## Files Included

The Question 1 directory contains the following files and folders:

```text
Question1/
├── Environment_Report.txt
├── README.md
└── screenshots/
    ├── Q1 - 01.png
    ├── Q1 - 02.png
    ├── Q1 - 03.png
    ├── Q1 - 04.png
    ├── Q1 - 05.png
    ├── Q1 - 06 .png
    └── Q1 -07 .png
```

The `screenshots` directory contains evidence of the commands executed in Google Cloud Shell and their corresponding outputs.

---

## Conclusion

The Linux environment was successfully inspected using standard command-line utilities. The current user, associated groups, shell environment, working directory, workspace contents, and network connectivity were verified.

The collected information was stored in `Environment_Report.txt`, and screenshots were included as evidence of command execution and output.

