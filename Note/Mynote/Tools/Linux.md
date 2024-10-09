# UNIX Commands

## Table Content
- [File Management](#file-management)
- [System Management](#system-management)
- [Network Management](#network-management)
- [Disk Management](#disk-management)
- [Process Management](#process-management)
- [User Management](#user-management)
- [Other](#other)
- [Basic Piping](#basic-piping)

## File Management
- `ls` : List directory
- `cd` : Change directory
- `pwd` : Present working directory
- `cp` : Copy file or directory
- `mv` : Move or rename file or directory
- `mkdir` : Make a new directory
- `rm` : Remove file
- `rmdir` : Remove an empty directory
- `touch` : Create an empty file
- `cat` : Concatenate and display file content
- `chmod` : Change file permissions
- `chown` : Change file ownership

## System Management
- `sudo` : Execute a command as the superuser
- `kill` : Terminate the process
- `free` : Display memory usage
- `uname -r` : Show system info
- `top` : Display Linux tasks
- `ps` : Display current processes
- `df` : Show free disk space
- `ds` : Display disk space usage
- `uptime` : Show how long the system has been running
- `shutdown` : Shutdown or restart the system
- `apt-get` : Install and update software packages

## Network Management
- `ping` : Echo the request to host
- `ifconfig` : Configure network interface
- `ip` : Manipulate routing, devices, policy routing, and tunnels
- `wget` : Download file from web
- `curl` : Transfer data to/from a server
- `ssh` : Secure shell (remote login)
- `scp` : Secure copy (transfer file between systems)
- `netstat` : Show network status

## Disk Management
- `fdisk` : Partition a hard drive
- `mkfs` : Create a file system
- `mount` : Mount file system
- `umount` : Unmount file system

## Process Management
- `ps` : List processes
- `top` : Display real-time process information
- `kill` : Kill a process by ID
- `killall` : Kill processes by name

## User Management
- `useradd` : Add a new user
- `passwd` : Change user password
- `usermod` : Modify a user account
- `userdel` : Delete a user account

## Other
- `man` : Display the manual for a command
- `history` : Show command history
- `alias` : Create shortcut for a command
- `grep` : Search text using patterns
- `echo` : Display a line of text
- `awk` : Pattern scanning & processing language
- `sed` : Stream editor
- `cron` : Automate tasks with scheduled commands

## Basic Piping
- Example: `ls | wc -l` : List all files and count the number of lines
- Redirection: `ls | grep ".txt" > textfiles.txt` : Redirect the output to a file
