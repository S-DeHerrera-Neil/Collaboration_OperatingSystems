## Persistence
```
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
```
```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
```
```
HKEY_USER\<SID>\Software\Microsoft\Windows\CurrentVersion\Run
```
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services
```
Note: run `services.msc` to view running services and search for malicious services

## Microsoft Edge URL History
```
HKEY_CLASSES_ROOT\Local Settings\Software\Microsoft\Windows\CurrentVersion\AppContainer\Storage\microsoft.microsoftedge_8wekyb3d8bbwe\Children\001\Internet Explorer\DOMStorage
```

## USB History
```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\USB
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\USBSTOR
```
## MRU (Most Recently Used) history
```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\ComDlg32\OpenSavePidlMRU
```

## Recent Files
```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs
```

## Windows User Profiles
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList
```
Note: to get account names and their SIDs side-by-side run the powershell command:

`Get-Wmiobject win32_useraccount | Format-Table Name, SID`


## Network Profiles (history of wifi connections)
```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Profiles
```
