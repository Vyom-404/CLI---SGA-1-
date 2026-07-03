# Question 5 - Storage Health Assessment and Documentation

## Objective

The objective of this task is to assess the storage resources of the Linux environment before deployment of a new application server.

The assessment includes identifying available storage devices, mounted file systems, disk usage statistics, inode utilization, storage health observations, and recommendations for improving storage utilization.

The required `Storage_Assessment_Report.txt` file was created using the `vi` editor.

---

## Command 1

```bash
cd ~/Graded_Lab_Assignment
```

### Observation

This command changed the current working directory to the main `Graded_Lab_Assignment` directory.

This ensured that the Question 5 folder was created inside the assignment repository.

---

## Command 2

```bash
mkdir -p Question5/screenshots
```

### Observation

This command created the `Question5` directory along with a `screenshots` subdirectory.

The screenshots directory is used to store evidence of storage-related command outputs and `vi` editor operations.

---

## Command 3

```bash
cd Question5
```

### Observation

This command changed the current working directory to the `Question5` directory.

All subsequent commands for the storage health assessment were executed from this directory.

---

## Command 4

```bash
lsblk
```

### Observation

The `lsblk` command displayed the available block storage devices in the Linux environment.

The output provided information such as:

- Device names
- Device sizes
- Device types
- Mount points

This command was used to identify the available storage devices.

---

## Command 5

```bash
findmnt
```

### Observation

The `findmnt` command displayed the mounted file systems in the Linux environment.

The output provided information about:

- Mount points
- Source devices
- File system types
- Mount options

This command was used to inspect the file systems currently mounted in the environment.

---

## Command 6

```bash
df -h
```

### Observation

The `df -h` command displayed disk usage statistics in human-readable format.

The output included:

- Total file system size
- Used storage space
- Available storage space
- Usage percentage
- Mount points

The `-h` option displayed storage sizes using readable units such as MB and GB.

---

## Command 7

```bash
df -i
```

### Observation

The `df -i` command displayed inode utilization for mounted file systems.

The output included:

- Total number of inodes
- Used inodes
- Available inodes
- Inode usage percentage
- Mount points

This information is important because a file system can become unable to create new files if all inodes are exhausted, even when free disk space remains available.

---

## Command 8

```bash
vi Storage_Assessment_Report.txt
```

### Observation

This command opened the `vi` editor and created the required `Storage_Assessment_Report.txt` file.

The report was prepared using the `vi` editor as required by the assignment.

---

## vi Editor Operation 1

```text
i
```

### Observation

The `i` key changed the `vi` editor to Insert mode.

Insert mode allowed report content to be entered into `Storage_Assessment_Report.txt`.

The report documented:

- Available storage devices
- Mounted file systems
- Disk usage statistics
- Inode utilization
- Storage health observations
- Recommendations for improving storage utilization

---

## vi Editor Operation 2

```text
Esc
```

### Observation

The `Esc` key exited Insert mode and returned the `vi` editor to Normal mode.

This allowed a save-and-exit command to be entered.

---

## vi Editor Operation 3

```text
:wq
```

### Observation

The `:wq` command saved the contents of `Storage_Assessment_Report.txt` and exited the `vi` editor.

The `w` operation wrote the changes to the file, while the `q` operation closed the editor.

---

## Command 9

```bash
cat Storage_Assessment_Report.txt
```

### Observation

The `cat` command displayed the contents of `Storage_Assessment_Report.txt` directly in the terminal.

This verified that the storage assessment report had been successfully created and saved.

---

## Command 10

```bash
ls -l Storage_Assessment_Report.txt
```

### Observation

This command displayed file information for `Storage_Assessment_Report.txt`.

The output confirmed that the required report file existed and showed details such as permissions, ownership, file size, and modification time.

---

## Available Storage Devices

Available block storage devices were investigated using:

```bash
lsblk
```

The command displayed the block devices available in the environment together with their sizes, types, and mount information.

This information helps identify the storage resources available for operating system files, application data, logs, and other server requirements.

---

## Mounted File Systems

Mounted file systems were investigated using:

```bash
findmnt
```

The output showed the relationship between mounted file systems and their mount points.

Mounted file system information is important because applications depend on accessible file systems for binaries, configuration files, application data, logs, and temporary storage.

---

## Disk Usage Statistics

Disk usage was investigated using:

```bash
df -h
```

The command displayed storage capacity and utilization in human-readable format.

Important fields included:

| Field | Meaning |
|---|---|
| `Size` | Total file system capacity |
| `Used` | Storage space currently used |
| `Avail` | Storage space currently available |
| `Use%` | Percentage of storage capacity used |
| `Mounted on` | File system mount point |

Monitoring disk usage helps identify file systems that may be approaching capacity.

---

## Inode Utilization

Inode utilization was investigated using:

```bash
df -i
```

Important fields included:

| Field | Meaning |
|---|---|
| `Inodes` | Total available inodes |
| `IUsed` | Number of used inodes |
| `IFree` | Number of free inodes |
| `IUse%` | Percentage of inodes used |
| `Mounted on` | File system mount point |

Inode monitoring is important because each file and directory requires inode resources.

A file system may still have free storage capacity but fail to create new files if inode resources are exhausted.

---

## Storage Health Observations

The storage environment was assessed by reviewing available block devices, mounted file systems, disk space utilization, and inode utilization.

The following technical observations were made:

1. Available storage devices can be identified using `lsblk`.

2. Active mounted file systems and their mount relationships can be inspected using `findmnt`.

3. Disk capacity and utilization can be monitored using `df -h`.

4. Inode consumption can be monitored using `df -i`.

5. High disk usage can reduce the space available for application data, logs, temporary files, updates, and system operations.

6. High inode utilization can prevent the creation of new files even when free disk capacity remains available.

7. Both disk capacity and inode availability should be monitored before and after application deployment.

---

## Recommendations for Improving Storage Utilization

The following recommendations can improve storage utilization:

1. Monitor disk usage regularly using `df -h`.

2. Monitor inode utilization regularly using `df -i`.

3. Remove unnecessary temporary files.

4. Delete or archive obsolete application logs.

5. Configure log rotation to prevent uncontrolled growth of log files.

6. Archive old application data that is no longer actively required.

7. Investigate file systems approaching high utilization.

8. Remove duplicate and unnecessary files where appropriate.

9. Maintain sufficient free storage capacity for future application growth.

10. Increase storage capacity when sustained utilization becomes high.

---

## Files Included

The Question 5 directory contains:

```text
Question5/
├── Storage_Assessment_Report.txt
├── README.md
└── screenshots/
```

The `screenshots` directory contains evidence of:

- Available storage device output
- Mounted file system output
- Disk usage statistics
- Inode utilization
- `vi` editor operations
- Final report verification

---

## Conclusion

The storage health assessment was completed using standard Linux storage utilities.

Available storage devices were investigated using `lsblk`, mounted file systems were inspected using `findmnt`, disk usage statistics were collected using `df -h`, and inode utilization was examined using `df -i`.

The required `Storage_Assessment_Report.txt` file was created and documented using the `vi` editor.

The assessment demonstrated the importance of monitoring both storage capacity and inode utilization. Regular monitoring, cleanup, log management, data archiving, and capacity planning are recommended to maintain efficient storage utilization and support reliable application deployment.
