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

