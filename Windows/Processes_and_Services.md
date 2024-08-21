# Windows Process and Service Searching via Terminal

## get-process and get-service (use get-ciminstance command whenever possible)

`get-process` grabs a table of all processes (similar to `tasklist`), get-process does NOT show Parent Process ID (PPID), instead use `get-ciminstance win32_process`

similarly `get-service` grabs a table of all services sorted by name

### Syntax

```
get-process [-name "explorer,otherprocess,searchprocess"] [-Id "12345"]

get-service [-name "explorer,otherprocess,searchprocess"]
```
- `-name` this searches the processes for strings, to specify multiple search processes use a comma to delimit them
- `-Id` searches for a specific process Id (note: it may be easier to sort get-process by process Id instead) THIS DOES NOT WORK WITH get-service

### Examples

```
get-process | sort-object -property Id
```
This grabs all processes and sorts them by process ID

```
(get-process -Id "12345").modules
```
This grabs all attached modules and DLLs to a process

```
get-process -Name "myprocess" | select *

get-service -Name "myservice" | select *
```
This grabs all available information about a specific process or service

```
get-service | where-object {$_.Statues -cmatch "Running"}
```
This grabs all services that are running (Note: this is not relevant for processes as everthing provided by get-process and get-ciminstance is already running)

## get-ciminstance win32_process or get-ciminstance win32_service

`get-ciminstance win32_process` is similar to get-process with the benefit of being able to view Parent Process ID (PPID)

`get-ciminstance win32_service` is similar to the win32_process variant

### Syntax

```
get-ciminstance win32_process

get-ciminstance win32_service
```

### Examples

```
get-ciminstance win32_process | select ProcessID,Name,ParentProcessID | sort processID
```
Grabs a table of all process IDs, Names, and Parent Process IDs (PPID) and then sorts by processID

```
get-ciminstance win32_process | where-object {$_.Name -match "myprocess"} | select *

get-ciminstance win32_service | where-object {$_.Name -match "myservice"} | select *
```
Grabs all information for a process or service with a specified name

## Sysinternals tools

# Process and Service searching via GUI
`services.msc` a gui to view running services

# Process Persistence

## Net Start
- provides a list of all processes running at start up
```
net-start
``` 

## Get-ScheduledTask
- grabs all scheduled processes
```
Get-ScheduledTask
```  

# Networking

## netstat

`netstat` is a CMD command that provides a status of all ports on the machine, the powershell equivalent is 
`Get-NetTCPConnection`

Note: since this is a CMD command so it only returns an array of strings and not an object, any further filtering must done via regex

### syntax
CMD
```
netstat -ano
```
- `-a` shows all ports
- `-n` displays addresses in numerical form
- `-o` displays the process responsible for each connection or listening port
- `-p "TCP"` shows all TCP connections and listening ports (you can also search for UDP)

## Get-NetTCPConnection or Get-Net
(PowerShell)
- command that provides a status of all ports on the machine
```
Get-NetTCPConnection
``` 

### Syntax

(PowerShell)
```
Get-NetTCPConnection
```
- searches for all TCP connections with a state of closed, can also search for "Listen", "Established", etc
```
-State "Closed"
``` 
