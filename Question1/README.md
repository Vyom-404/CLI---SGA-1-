# Question 1 - Linux Environment Verification

## Objective

The objective of this task is to verify the Linux environment by checking the current user account, associated groups, current shell, working directory, workspace contents, and network connectivity.

The collected information is stored in `Environment_Report.txt`, and screenshots are included as evidence of command execution and output.

---

## Command 1

```bash
mkdir -p Graded_Lab_Assignment/Question1/screenshots
```

### Observation

This command created the required assignment directory structure. The `-p` option ensured that parent directories were created if they did not already exist.

The `screenshots` directory was created to store evidence of the commands executed for Question 1.

---

## Command 2

```bash
cd Graded_Lab_Assignment/Question1
```

### Observation

This command changed the current working directory to the `Question1` directory.

All subsequent Question 1 commands and files were managed from this directory.

---

## Command 3

```bash
whoami
```

### Observation

The `whoami` command displayed the username of the currently logged-in user.

**Output observed:** `vyomg20082005`

This verified the active Linux user account in the Google Cloud Shell environment.

---

## Command 4

```bash
groups
```

### Observation

The `groups` command displayed all groups associated with the current user account.

These groups represent the group memberships assigned to the active Linux user and may affect user permissions and access rights.

---

## Command 5

```bash
echo $SHELL
```

### Observation

This command displayed the default shell configured for the current user account.

The shell is responsible for interpreting and executing commands entered in the terminal.

---

## Command 6

```bash
pwd
```

### Observation

The `pwd` command displayed the absolute path of the current working directory.

This confirmed the exact directory location from which the Question 1 commands were being executed.

---

## Command 7

```bash
ls -la
```

### Observation

The `ls -la` command listed all files and directories in the current workspace, including hidden files and directories.

It also displayed detailed information such as:

- File permissions
- Number of links
- File owner
- Group owner
- File size
- Last modification date and time

This command helped inspect the contents and structure of the current workspace.

---

## Command 8

```bash
ping -c 4 google.com
```

### Observation

This command tested network connectivity by sending four ICMP packets to `google.com`.

The `-c 4` option limited the command to four packets.

Successful responses confirmed that the Linux environment had working network connectivity.

---

## Command 9

```bash
{
  echo "LINUX ENVIRONMENT VERIFICATION REPORT"
  echo "====================================="
  echo
  echo "1. Username"
  whoami
  echo
  echo "Groups Associated with Account"
  groups
  echo
  echo "2. Current Shell"
  echo "$SHELL"
  echo
  echo "3. Current Working Directory"
  pwd
  echo
  echo "4. Files and Directories in Workspace"
  ls -la
  echo
  echo "5. Network Connectivity Verification"
  ping -c 4 google.com
} > Environment_Report.txt
```

### Observation

This grouped command collected the required Linux environment information and redirected the complete output into `Environment_Report.txt`.

The report included:

- Current username
- Associated groups
- Current shell
- Current working directory
- Files and directories in the workspace
- Network connectivity verification

The `>` redirection operator created or overwrote `Environment_Report.txt` with the collected report output.

---

## Command 10

```bash
cat Environment_Report.txt
```

### Observation

The `cat` command displayed the contents of `Environment_Report.txt` directly in the terminal.

This confirmed that the required Linux environment information had been successfully collected and stored in the report file.

---

## Final Directory Structure

The Question 1 directory contains the environment report, documentation, and screenshots:

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

---

## Conclusion

The Linux environment was successfully verified using standard command-line utilities.

The active user account, associated groups, shell environment, current working directory, workspace contents, and network connectivity were inspected successfully.

The collected information was stored in `Environment_Report.txt`, and screenshots were included as evidence of the commands executed and their corresponding outputs.
