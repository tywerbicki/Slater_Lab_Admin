# Slater Lab Administration

This repository contains a collection of shell scripts (sensitive scripts omitted) that I use to help monitor and manage the Slater Lab compute environment:

* [Backup](#backup)
* [Scan Permissions](#scan-permissions)
* [Query Jobs](#query-jobs)
* [*Additional Useful Commands*](#additional-useful-commands)

---

## Backup
 
Scan recursively `TARGET_DIR` and all of its sub-directories except those specified in the `OMIT_DIRS` array. Any file with a `.sh`, `.py`, `.slurm`, `.R`, `.c`, or `.cpp` extension is copied and stored in a compressed tarball located in `BACKUP_DIR`.

---

## Scan Permissions

Scan recursively `TARGET_DIR` and all of its sub-directories except those specified in the `OMIT_DIRS` array up to a maximum depth of `MAX_DEPTH`. This script generates 3 deliverables, all of which are stored in `DEPOSIT_DIR`:

1) *wrong_group.txt*

    * A text file containing a list of all file names with an incorrectly specified group.
    
2) *bad_permissions.txt*

    * A text file containing a list of all file names that are accessible to 'other users'.
    
3) *report.txt*

    * A text file containing a miniature *report* for each user specified in the `USERS` array. Each report lists the number of files owned by that user that have an incorrectly specified group, as well as the number of files owned by that user that are accessible to 'other users'.

---

## Query Jobs

Deposits *jobs_report.txt* in `DEPOSIT_DIR`, which lists the number of pending and running jobs for each user specified in the `USERS` array.

---

## Additional Useful Commands

* Retrieve a sorted list of the `N`-1 largest directories by disk usage in directory `FOLDER`:

    > `du -h --max-depth=1 <FOLDER> | sort -hr | head -n <N>` 

---
