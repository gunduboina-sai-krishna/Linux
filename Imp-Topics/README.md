## Load Average:

**Load average** refers to the average number of processes that are either:

actively using the CPU (running), or waiting to use the CPU (runnable state),over a specific time period.

If you have 4 cores:

Load average of 4.00 = fully utilized

Load average of 2.00 = 50% load

Load average of 6.00 = overloaded (50% more demand than capacity)

load average: 4.45, 4.75, 4.65

These three numbers represent the average system load over the last 1min - 4.45 load, 5 - 4.75 load, and 15 minutes - 4.65 load, respectively.

## Run Level:

- Runlevels define the state or mode that the Linux system is running in.Each runlevel determines which services and processes are started or stopped.

| Runlevel | Meaning     | Description                              |
| -------- | ----------- | ---------------------------------------- |
| 0        | Halt        | System shutdown                          |
| 1        | Single-user | Maintenance mode (no networking)         |
| 2        | Multi-user  | No NFS/network filesystems               |
| 3        | Multi-user  | Full multi-user with networking (no GUI) |
| 4        | Unused      | Custom (rarely used)                     |
| 5        | Graphical   | Multi-user with GUI                      |
| 6        | Reboot      | Restart the system                       |

**change Runlevel**

```
Old Way:
init 3
init 5

modern Way:

systemctl isolate multi-user.target -- N 3
systemctl isolate graphical.target -- N 5
```

## Inode:

- An inode (index node) is a data structure in Linux filesystems that stores metadata about a file — not the file name itself.
- You can run out of inodes even if disk space is free (too many small files). -- command (df -i - Shows how many inodes are used/free per filesystem)

## Logrotation:

- Log rotation is the process of automatically managing log files so they don’t grow too large and fill up the disk.
      - Renames or compresses the old log file (e.g., access.log.1, access.log.2.gz)
      - Creates a new empty log file to continue logging.
      - Optionally deletes old logs after a set number of rotations.
- Controlled by - **/etc/logrotate.conf and /etc/logrotate.d/** 

## Find Vs Locate

| Feature            | `find`                           | `locate`                  |
| ------------------ | -------------------------------- | ------------------------- |
| **Search type**    | Real-time filesystem scan        | Pre-built database        |
| **Speed**          | Slower                           | Very fast                 |
| **Accuracy**       | Always current                   | May be outdated           |
| **Requires root?** | No                               | Needs root for `updatedb` |
| **Filtering**      | Very powerful (size, date, name, time etc.) | Name-based only           |
| **Common use**     | Admin scripts, automation        | Quick manual lookups      |

## What are SUID, SGID, and Sticky Bit

| Feature        | Applies To | Purpose                                | Example                |
| -------------- | ---------- | -------------------------------------- | ---------------------- |
| **SUID(set User ID)**       | File(u+s)       | Run as file **owner**                  | `/usr/bin/passwd`      |
| **SGID(set Group ID)**       | File / Dir(g+s) | Run as file **group** or inherit group | Shared project folders |
| **Sticky Bit** | Directory  | Only owner can delete their files(+t)      | `/tmp` directory       |

**Numeric Representation**
| Special Bit | Octal Value |
| ----------- | ----------- |
| SUID        | 4xxx        |
| SGID        | 2xxx        |
| Sticky Bit  | 1xxx        |

**Check package repo and gpg keys**
- ``` sudo apt-cache policy ``` - list all apt repositories
- ``` ls -l /etc/apt/sources.list.d ``` - lists the added packages
- ``` apt-key list ``` - to check for GPG keys
- ``` ls /etc/apt/trusted.gpg.d/ ``` 


