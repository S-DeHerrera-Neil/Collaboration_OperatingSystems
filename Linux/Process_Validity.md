# Live Process Viewing

### htop (recommended)

Pretty view of live processes, use F1-10 keys to modify display. (Use F2 then go to columns to add PPID)

### top (basic cmd)

A worse version of htop, may work on less advanced systems


# Identifying Orphans

Orphan life-cycle
1. Start with a parent with a high PPID
2. Parent process dies
3. Process becomes batman
4. Process gets PPID of 1 (init)

Note: If you are using the tree view the process will fall under `/home/orphan`

# Search for a process manually
```
ps -elf | grep "searchname"
```

# Check if system is SysV or Systemd

```
ps -p 1
```
grabs the process details for the process with PID 1

if this process is called "init" it is a SysV system, if the process is called "systemd" it is a systemd system

# Systemd

Common with more modern operating systems and uses `systemctl` for service management


### Syntax
```
systemctl <action> <service>
```
Actions: `list-units [-all]`, `start`, `stop`

# SysV

Older service management system that uses the `service` command

### Syntax
```
service <service> <action>
```
Actions: `status`, `start`, `stop`, `restart`

# File Handles and Descriptors

### lsof
```
sudo lsof -c <process>
```
List all open files for a specific process

### Format
| COMMAND | PID | USER | FD | TYPE | DEVICE | SIZE/OFF | NODE | NAME |
| :------ | ----- | -------- | --- | ---- | -------- | ------------ | --------| ----------------------|
| sshd | 1963 | student | 0u | CHR | 1,3 | 0t0 | 1028 | /dev/null |
| sshd | 1963 | student | 1u | CHR | 1,3 | 0t0 | 1028 | /dev/null |
| sshd | 1963 | student | 2u | CHR | 1,3 | 0t0 | 1028 | /dev/null |
| sshd | 1963 | student | 3u | IPv4 | 12124 | 0t0 | TCP | *:ssh (LISTEN) |
| sshd | 1963 | student | 4u | IPv6 | 12126 | 0t0 | TCP | *:ssh (LISTEN) |

FD:File descriptor, shows permissions. u = read & write, r = read, and w = write.
