# Windows Process Validation'

## get-process (use get-ciminstance command whenever possible)

`get-process` grabs a table of all processes (similar to `tasklisk`), get-process does NOT show Parent Process ID (PPID), instead use `get-ciminstance win32_process`

### Syntax

```
get-process [-name "explorer,otherprocess,searchprocess"] [-Id "12345"]
```
- `-name` this searches the processes for strings, to specify multiple search processes use a comma to delimit them
- `-Id` searches for a specific process Id (note: it may be easier to sort get-process by process Id instead)

### Examples

```
get-process | sort-object -property Id
```
This grabs all processes and sorts them by process Id

```
(get-process -Id "12345").modules
```
This grabs all attached modules and DLLs to a process


```
get-process -Name "myprocess" | select *
```
This grabs all available information about a specific process

## get-ciminstance win32_process

`get-ciminstance win32_process` is similar to get-process with the benefit of being able to view Parent Process ID (PPID)

### Syntax

```
get-ciminstance win32_process
```

### Examples

```
get-ciminstance win32_process | select ProcessID,Name,ParentProcessID | sort processID
```
Grabs a table of all process IDs, Names, and Parent Process IDs (PPID) and then sorts by processID

```
get-ciminstance win32_process | where-object {$_.Name -match "myprocess"} | select *
```
Grabs all information for a process with a specified name
