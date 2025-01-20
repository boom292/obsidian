---
aliases:
  - MBR
  - Master Boot Record
  - GUID Partition Table
  - GPT
---
3rd Jul '24, 11:58am

Status: #InProgress #ProperNotes 

Tags: [[BIOS]] [[Configuring BIOS or CMOS]] [[OS]] [[Boot Up]]

# Disk Partitioning

**Disk partitioning** or **disk slicing** is the creation of one or more regions on secondary storage, so that each region can be managed separately. These regions are called partitions. It is typically the first step of preparing a newly installed disk after a partitioning scheme is chosen for the new disk before any file system is created.

The disk stores the information about the partitions' locations and sizes in an area known as the partition table that the operating system reads before any other part of the disk. Each partition then appears to the operating system as a distinct "logical" disk that uses part of the actual disk.

Partitioning allows the use of different filesystems to be installed for different kinds of files. Separating user data from system data can prevent the system partition from becoming full and rendering the system unusable. Partitioning can also make backing up easier. A disadvantage is that it can be difficult to properly size partitions, resulting in having one partition with too much free space and another nearly totally allocated.

## File Systems

Most operating systems store all the files (system and os) in one partition, some unix based operating systems use one more partition for swap. 

# References
https://wiki.osdev.org/MBR_(x86)