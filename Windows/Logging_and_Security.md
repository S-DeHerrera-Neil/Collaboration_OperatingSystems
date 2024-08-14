# Log locations
## Registry commands
- cmd: `reg query "<key>"`
- powershell: `Get-ItemProperty "<key>"`

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

This returns the path of an executable and it's last execution time

Version 1809* (Windows Build 10.0.17763) and newer:
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\bam\State\UserSettings
```

Version 1803* (Windows Build 10.0.17134) and below:
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\bam\UserSettings
```

*Note: you can get windows version by running `systeminfo` (cmd) or `get-computerinfo | select osname, osversion` (powershell)

\## Recycle Bin
