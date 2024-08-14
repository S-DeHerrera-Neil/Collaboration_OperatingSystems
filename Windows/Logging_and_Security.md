# Log locations
### Commands to know
- cmd: `reg query "<key>"`
- powershell: `Get-ItemProperty "<key>"`
- sysinternals: `findstr <searchfile> --accepteula` CONFIRM THIS SYNTAX

## User Assist
Used for file and shortcut access history
```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\<GUID>\Count\
HKEY_USERS\<SID>\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\<GUID>\Count\
```
```
CEBFF5CD-ACE2-4F4F-9178-9926F41749EA # GUID to search for accessed applications and files
F4E57C4B-2036-45F0-A9AB-443BCFE33D9F # GUID to search for shortcuts used to start programs
```
Note: All UserAssist registry data is encoded with [ROT13](https://rot13.com/) (link to decode)

## Windows Background Activity Moderator (BAM)
Windows service that controls activity of background apps (only windows 10 version 1709 and after)

This registry holds the path to the executable

Version 1809* (Windows Build 10.0.17763) and newer:
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\bam\State\UserSettings
```

Version 1803* (Windows Build 10.0.17134) and below:
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\bam\UserSettings
```

*Note: you can get windows version by running `systeminfo` (cmd) or `get-computerinfo | select osname, osversion` (powershell)

## Recycle Bin

```
C:\$Recycle.bin
```

Contains folder's for each SID

Format:
- `$RXXXXXX` - content of deleted file
- `$IXXXXXX` - original path and name

## Prefetch
Files created when a program is first run and persist between restarts (limit of 1024 files on Win10 and 128 on Win7)

Prefetch stores the last 8 execution times
```
C:\Windows\Prefetch
```

## Jump Lists
Stores:
- First execution time
- Creation Time
- Last Execution
- Modification time

```
C:\Users\<SID>\AppData\Roaming\Microsoft\Windows\Recent
```
## Recent Files
tracks the last 150 files and folders opened

holds path, entry, and modification time
```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs
HKEY_USERS\<SID>\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs
```

## Browser Artifacts

Chrome (URL history, current session/tabs, top sites):
```
C:\Users\<USER>\AppData\Local\Google\Chrome\User Data\Default\history
```

## Auditing

```
Rt click <file> on the desktop > Properties > Security > Advanced > Auditing > Continue > Add > Select a Principle > Type <username> (andy.dwyer) > Check Names > Ok >  Full Control > Ok > Apply > Ok
```
more review needed

## Viewing Windows Events

Registry
```
HKEY_LOCAL_MACHINE\SECURITY\Policy\PolAdtEv
```

### Method 1: EventViewer GUI
run `eventvwr` in cmd to open the application

### Method 2: Powershell
log viewer:
```
Get-Eventlog
Get-WinEvent
```

### Method 3: CMD
log viewer:
```
wevutil
```

Audity policy viewing and editing:
```
auditpol
```
more research needed

### Common Event Codes

| Name | ID | Level | EventLog |
| ---- | -- | ----- | -------- |
| Account Lockouts | 4740 | Informational | Security |
| User Added to Privileged Group | 4728, 4732, 4756 | Informational | Security |
| Security-Enabled group Modification | 4735 | Informational | Security |
| Successful User Account Login | 4624 | Informational | Security |
| Failed User Account Login | 4625 | Informational | Security |
| Account Login with Explicit Credentials | 4648 | Informational | Security |
| Event Log was Cleared | 104 | ----- | -------- |
| Audit Log was Cleared | 1102 | ----- | Security |
| System audit policy was changed | 4719 | ----- | -------- |
| PS Module Logging (Command Execution) | 4103 | ----- | -------- |
| PS Script-Block Logging (Script Execution) | 4104,4105,4106 | ----- | -------- |
