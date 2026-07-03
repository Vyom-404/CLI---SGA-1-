# Question 3 - File System and Link Analysis

## Objective

The objective of this task is to create a file, a hard link, and a symbolic link and investigate their behavior in Linux.

The experiment compares inode numbers, link behavior, metadata, and the effect of deleting the original file.

---

## Command 1

```bash
cd ~/Graded_Lab_Assignment
```

### Observation

This command changed the current working directory to the main `Graded_Lab_Assignment` directory.

This ensured that the Question 3 folder was created inside the assignment repository.

---

## Command 2

```bash
mkdir -p Question3/screenshots
```

### Observation

This command created the `Question3` directory along with the `screenshots` subdirectory.

The screenshots directory is used to store evidence of command execution and output.

---

## Command 3

```bash
cd Question3
```

### Observation

This command changed the current working directory to the `Question3` directory.

All subsequent commands for the file system and link analysis were executed from this directory.

---

## Command 4

```bash
echo "This is the original project file." > original.txt
```

### Observation

This command created a file named `original.txt` and stored sample text inside it.

The `>` redirection operator wrote the specified text into the file.

---

## Command 5

```bash
cat original.txt
```

### Observation

This command displayed the contents of `original.txt`.

The output confirmed that the original file had been created successfully with the expected text.

---

## Command 6

```bash
ln original.txt hardlink.txt
```

### Observation

This command created a hard link named `hardlink.txt` for `original.txt`.

The hard link refers to the same inode and underlying file data as the original file.

---

## Command 7

```bash
ln -s original.txt symlink.txt
```

### Observation

This command created a symbolic link named `symlink.txt` pointing to `original.txt`.

Unlike a hard link, the symbolic link stores a reference to the target file path.

---

## Command 8

```bash
ls -li
```

### Observation

This command displayed files and directories together with their inode numbers.

The output showed that `original.txt` and `hardlink.txt` shared inode number `131768`, while `symlink.txt` had a different inode number `131769`.

---

## Command 9

```bash
stat original.txt hardlink.txt symlink.txt
```

### Observation

The `stat` command displayed detailed metadata for the original file, hard link, and symbolic link.

The output confirmed that `original.txt` and `hardlink.txt` shared inode `131768`, while `symlink.txt` used inode `131769`.

---

## Command 10

```bash
cat hardlink.txt
```

### Observation

This command displayed the contents through the hard link before deletion of the original filename.

The output matched the contents of `original.txt`, confirming that the hard link accessed the same file data.

---

## Command 11

```bash
cat symlink.txt
```

### Observation

This command displayed the contents through the symbolic link before deletion of the original file.

The symbolic link successfully accessed the target because `original.txt` still existed at that time.

---

## Command 12

```bash
rm original.txt
```

### Observation

This command deleted the original filename `original.txt`.

The experiment then tested whether the hard link and symbolic link remained usable.

---

## Command 13

```bash
ls -li
```

### Observation

This command displayed the remaining files and their inode numbers after deleting `original.txt`.

The hard link remained with inode `131768`, while `symlink.txt` still existed as a symbolic link pointing to the now-missing `original.txt`.

---

## Command 14

```bash
cat hardlink.txt
```

### Observation

This command displayed the contents of `hardlink.txt` after deleting the original filename.

The content remained accessible because the hard link still referenced inode `131768` and the underlying file data.

---

## Command 15

```bash
cat symlink.txt
```

### Observation

This command attempted to access the symbolic link after deletion of `original.txt`.

The command produced an error because the symbolic link still pointed to `original.txt`, but that target path no longer existed.

---

## Command 16 - Generate Link Analysis Report

```bash
{
  echo "FILE SYSTEM AND LINK ANALYSIS REPORT"
  echo "===================================="
  echo
  echo "1. Inode Numbers of Files"
  echo "Original file inode before deletion: 131768"
  echo "Hard link inode: 131768"
  echo "Symbolic link inode: 131769"
  echo
  echo "2. Comparison Between Hard Link and Symbolic Link"
  echo "The hard link shared the same inode number as the original file."
  echo "The symbolic link had a different inode number and stored a path to the original file."
  echo
  echo "3. Effect of Deleting the Original File"
  echo "The hard link remained accessible after deleting the original file."
  echo "The symbolic link became broken because its target path no longer existed."
  echo
  echo "4. Metadata Collected Using Linux Utilities"
  stat hardlink.txt symlink.txt
  echo
  echo "5. Conclusions Drawn from the Experiment"
  echo "Hard links remain usable after the original filename is deleted because they reference the same inode and file data."
  echo "Symbolic links depend on the target path and become broken when the target file is deleted."
} > Link_Analysis_Report.txt
```

### Observation

This grouped command generated the required `Link_Analysis_Report.txt` file.

The report recorded inode numbers, the comparison between hard and symbolic links, deletion behavior, metadata, and conclusions from the experiment.

---

## Command 17

```bash
cat Link_Analysis_Report.txt
```

### Observation

This command displayed the contents of `Link_Analysis_Report.txt` in the terminal.

The output verified that the required link analysis information had been successfully recorded in the report.

---

## Inode Number Analysis

The inode numbers observed during the experiment were:

| File | Inode Number |
|---|---:|
| `original.txt` | `131768` |
| `hardlink.txt` | `131768` |
| `symlink.txt` | `131769` |

The original file and hard link shared the same inode number. This confirmed that both filenames referred to the same underlying file data.

The symbolic link had a different inode number because it was a separate file containing a reference to the target path.

---

## Comparison Between Hard Link and Symbolic Link

| Feature | Hard Link | Symbolic Link |
|---|---|---|
| Inode | Same as original file | Different from original file |
| Observed inode | `131768` | `131769` |
| Reference type | References same file data | References target path |
| After original deletion | Remained accessible | Became broken |

A hard link is another directory entry for the same inode. Therefore, deleting one filename does not remove the underlying data while another hard link still exists.

A symbolic link is a separate file that stores a path to another file. If the target path is deleted, the symbolic link becomes broken.

---

## Effect of Deleting the Original File

After executing:

```bash
rm original.txt
```

the hard link continued to display:

```text
This is the original project file.
```

This occurred because `hardlink.txt` still referenced inode `131768`.

The symbolic link no longer worked because it pointed to the deleted path `original.txt`.

---

## Metadata Collected Using Linux Utilities

Metadata was collected using the `stat` command:

```bash
stat original.txt hardlink.txt symlink.txt
```

Before deletion, the observed metadata showed:

```text
original.txt inode: 131768
hardlink.txt inode: 131768
symlink.txt inode: 131769
```

The original file and hard link also showed a link count of `2` before deletion, confirming that two directory entries referenced the same inode.

The symbolic link showed a separate inode and was identified as a symbolic link.

---

## Summary of Findings

The experiment demonstrated the following findings:

1. `original.txt` and `hardlink.txt` shared the same inode number `131768`.

2. `symlink.txt` had a separate inode number `131769`.

3. The hard link accessed the same file data as the original file.

4. The symbolic link accessed the original file through its target path.

5. After deleting `original.txt`, `hardlink.txt` remained usable.

6. After deleting `original.txt`, `symlink.txt` became broken because its target path no longer existed.

---

## Conclusion

The experiment successfully demonstrated the difference between hard links and symbolic links in Linux.

A hard link shares the same inode and underlying file data as the original file. Therefore, deleting the original filename does not remove the data as long as another hard link still exists.

A symbolic link has its own inode and stores a reference to the target path. When the original target file is deleted, the symbolic link becomes broken.

The results confirm that hard links are independent of the original filename, while symbolic links depend on the continued existence of their target path.
