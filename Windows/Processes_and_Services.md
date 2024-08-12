# Windows Process Validation

## get-process

`get-process` grabs a table of all processes (similar to `tasklisk`)

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
