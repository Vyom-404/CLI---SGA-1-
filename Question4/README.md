# Question 4 - File Access and I/O Investigation

## Objective

The objective of this task is to investigate file access and input/output operations in Linux for an application experiencing logging issues.

The investigation includes identifying open files, observing file descriptors, testing output and error redirection, examining resource limits, and explaining how Linux manages file I/O.

---

## Command 1

```bash
cd ~/Graded_Lab_Assignment
```

### Observation

This command changed the current working directory to the main `Graded_Lab_Assignment` directory.

This ensured that the Question 4 folder was created inside the assignment repository.

---

## Command 2

```bash
mkdir -p Question4/screenshots
```

### Observation

This command created the `Question4` directory along with a `screenshots` subdirectory.

The screenshots directory is used to store evidence of command execution and output.

---

## Command 3

```bash
cd Question4
```

### Observation

This command changed the current working directory to the `Question4` directory.

All subsequent commands for the file access and I/O investigation were executed from this directory.

---

## Command 4

```bash
lsof | head -20
```

### Observation

This command attempted to list open files using the `lsof` utility.

The command produced the following error:

```text
-bash: lsof: command not found
```

This showed that the `lsof` utility was not installed in the current Google Cloud Shell environment. Therefore, the Linux `/proc` filesystem was used for the investigation instead.

---

## Command 5

```bash
find /proc/$$/fd -maxdepth 1 -type l -exec ls -l {} \;
```

### Observation

This command identified open file descriptors associated with the current shell process.

The `$$` variable represents the process ID of the current shell, while `/proc/$$/fd` contains symbolic links representing open file descriptors.

This provided a method to investigate open files without using the unavailable `lsof` utility.

---

## Command 6

```bash
ls -l /proc/$$/fd
```

### Observation

This command displayed the file descriptors associated with the current shell process.

Linux uses numeric file descriptors to represent open I/O streams and files.

Common standard file descriptors are:

- `0` - Standard Input
- `1` - Standard Output
- `2` - Standard Error

The output showed symbolic links representing the resources connected to the current shell file descriptors.

---

## Command 7

```bash
echo "Application log test successful" > output.log
```

### Observation

This command tested standard output redirection.

The `>` operator redirected the text produced by `echo` into the file `output.log`.

The command created the file if it did not already exist and stored the output inside it.

---

## Command 8

```bash
cat output.log
```

### Observation

This command displayed the contents of `output.log`.

**Output observed:**

```text
Application log test successful
```

This confirmed that standard output redirection had worked successfully.

---

## Command 9

```bash
ls /nonexistent_directory 2> error.log
```

### Observation

This command intentionally attempted to list a directory that did not exist.

The `2>` operator redirected standard error into the file `error.log`.

As a result, the error message was stored in the file instead of being displayed directly by the original `ls` command.

---

## Command 10

```bash
cat error.log
```

### Observation

This command displayed the contents of `error.log`.

**Output observed:**

```text
ls: cannot access '/nonexistent_directory': No such file or directory
```

This confirmed that standard error redirection had worked successfully.

---

## Command 11

```bash
ls /tmp /nonexistent_directory > combined.log 2>&1
```

### Observation

This command tested combined standard output and standard error redirection.

The `>` operator redirected standard output into `combined.log`.

The `2>&1` expression redirected standard error to the same destination as standard output.

Therefore, both successful output from `/tmp` and the error generated for `/nonexistent_directory` were stored in the same file.

---

## Command 12

```bash
cat combined.log
```

### Observation

This command displayed the contents of `combined.log`.

The output contained:

- An error message for `/nonexistent_directory`
- The directory listing of `/tmp`

This confirmed that both standard output and standard error had been redirected into the same file successfully.

---

## Command 13

```bash
ulimit -a
```

### Observation

The `ulimit -a` command displayed the resource limits applied to the current shell environment.

These limits control resources such as:

- Maximum number of open files
- Maximum number of user processes
- Stack size
- Core file size
- CPU time
- Virtual memory
- Locked memory

The observed output documented the resource restrictions and limits configured for the current Linux shell.

---

## Command 14 - Generate I/O Investigation Report

```bash
{
  echo "FILE ACCESS AND I/O INVESTIGATION REPORT"
  echo "========================================"
  echo
  echo "1. Open Files Identified"
  find /proc/$$/fd -maxdepth 1 -type l -exec ls -l {} \;
  echo
  echo "2. File Descriptor Observations"
  ls -l /proc/$$/fd
  echo
  echo "3. Output Redirection Result"
  cat output.log
  echo
  echo "4. Error Redirection Result"
  cat error.log
  echo
  echo "5. Combined Output and Error Redirection Result"
  cat combined.log
  echo
  echo "6. Resource Limits Observed"
  ulimit -a
  echo
  echo "7. Explanation of How Linux Manages File I/O"
  echo "Linux represents open files using file descriptors."
  echo "File descriptor 0 represents standard input, 1 represents standard output, and 2 represents standard error."
  echo "Output redirection sends standard output to a file using the > operator."
  echo "Error redirection sends standard error to a file using the 2> operator."
  echo "The 2>&1 expression redirects standard error to the same destination as standard output."
  echo "Linux applies resource limits to control resources such as open files, processes, memory, and CPU usage."
} > IO_Investigation_Report.txt
```

### Observation

This grouped command generated the required `IO_Investigation_Report.txt` file.

The report collected:

- Open files identified
- File descriptor observations
- Output redirection results
- Error redirection results
- Combined output and error redirection results
- Resource limits
- Explanation of Linux file I/O management

The `>` redirection operator stored the complete generated report in `IO_Investigation_Report.txt`.

---

## Command 15

```bash
cat IO_Investigation_Report.txt
```

### Observation

This command displayed the contents of `IO_Investigation_Report.txt` directly in the terminal.

The output verified that the required I/O investigation information had been successfully recorded in the report.

---

## Open Files Identified

Because `lsof` was unavailable in the environment, open files were investigated through the Linux `/proc` filesystem.

The directory:

```text
/proc/$$/fd
```

contains symbolic links representing file descriptors opened by the current shell process.

This allowed open I/O resources to be inspected without installing additional utilities.

---

## File Descriptor Observations

Linux represents open files and I/O streams using integer file descriptors.

The three standard descriptors are:

| File Descriptor | Name | Purpose |
|---|---|---|
| `0` | Standard Input | Receives input |
| `1` | Standard Output | Produces normal output |
| `2` | Standard Error | Produces error messages |

Additional file descriptors may be created when processes open files, pipes, sockets, or other I/O resources.

---

## Output Redirection Result

The following command redirected standard output:

```bash
echo "Application log test successful" > output.log
```

The resulting file contained:

```text
Application log test successful
```

This confirmed that the `>` operator successfully redirected standard output to a file.

---

## Error Redirection Result

The following command redirected standard error:

```bash
ls /nonexistent_directory 2> error.log
```

The resulting file contained:

```text
ls: cannot access '/nonexistent_directory': No such file or directory
```

This confirmed that `2>` successfully redirected standard error to a file.

---

## Combined Output and Error Redirection Result

The following command redirected both standard output and standard error:

```bash
ls /tmp /nonexistent_directory > combined.log 2>&1
```

The resulting `combined.log` file contained both:

- The error message generated for the nonexistent directory
- The successful directory listing generated for `/tmp`

This confirmed that `2>&1` redirected standard error to the same destination as standard output.

---

## Resource Limits Observed

Resource limits were inspected using:

```bash
ulimit -a
```

Linux resource limits help control how many system resources a process or user can consume.

These limits may include open files, processes, memory, CPU time, stack size, and other resources.

---

## Explanation of How Linux Manages File I/O

Linux manages file I/O using file descriptors.

When a process opens a file or I/O resource, the kernel provides a numeric file descriptor that the process uses for reading, writing, or other operations.

By default:

```text
0 = Standard Input
1 = Standard Output
2 = Standard Error
```

Output redirection changes the destination of standard output. The `>` operator can redirect standard output to a file.

Error redirection changes the destination of standard error. The `2>` operator redirects file descriptor `2` into a file.

The expression `2>&1` makes standard error use the same destination as standard output.

Linux also applies resource limits to control system resource usage. These limits help prevent individual processes or users from consuming excessive numbers of open files, processes, memory, or CPU resources.

---

## Technical Observations

1. The `lsof` utility was unavailable in the Google Cloud Shell environment.

2. The Linux `/proc` filesystem provided an alternative method for investigating open file descriptors.

3. Standard output was successfully redirected into `output.log`.

4. Standard error was successfully redirected into `error.log`.

5. Standard output and standard error were successfully combined inside `combined.log`.

6. File descriptors provided numeric references to open I/O streams and resources.

7. Resource limits were inspected using `ulimit -a`.

8. Linux file I/O is managed through kernel-maintained file descriptors and redirection mechanisms.

---

## Files Included

The Question 4 directory contains:

```text
Question4/
├── IO_Investigation_Report.txt
├── README.md
├── output.log
├── error.log
├── combined.log
└── screenshots/
```

---

## Conclusion

The file access and I/O investigation was completed successfully.

Open file descriptors were investigated through the Linux `/proc` filesystem because `lsof` was unavailable. Standard output, standard error, and combined redirection were tested successfully.

Resource limits were observed using `ulimit -a`, and the investigation demonstrated how Linux uses file descriptors to manage file I/O operations.

The final findings were documented in `IO_Investigation_Report.txt`, with screenshots included as evidence of command execution and output.
