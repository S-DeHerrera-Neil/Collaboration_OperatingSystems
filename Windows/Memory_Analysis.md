# Installing Notepad++
```
invoke-webrequest -uri "https://github.com/notepad-plus-plus/notepad-plus-plus/releases/download/v7.8.8/npp.7.8.8.Installer.x64.exe" -outfile "C:\npp.7.8.8.Installer.x64.exe" 
```
Download installer
```
start-process npp.7.8.8.Installer.x64.exe -ArgumentList '/S'
```
Run installer

# Installing Volatility
Use Powershell for all steps

```
invoke-webrequest -uri "invoke-webrequest -uri "http://downloads.volatilityfoundation.org/releases/2.6/volatility_2.6.win.standalone.zip"" -outfile "C:\Users\andy.dwyer\Desktop\Memory_Analysis\volatility_2.6_win64_standalone.zip"
```
Download standalone zip

```
Expand-Archive "C:\Users\andy.dwyer\Desktop\Memory_Analysis/volatility_2.6_win64_standalone.zip" "C:\Users\andy.dwyer\Desktop\Memory_Analysis\volatility_2.6_win64_standalone"
```
Unzip file

```
mv "C:\Users\andy.dwyer\Desktop\Memory_Analysis\volatility_2.6_win64_standalone\volatility_2.6_win64_standalone.exe" "C:\Users\andy.dwyer\Desktop\Memory_Analysis\volatility_2.6_win64_standalone.exe"
```
Moves executable to Memory Analysis folder

# Running Volatility

## THE ULTIMATE GUIDE TO VOLATILITY
https://github.com/volatilityfoundation/volatility/wiki/Command-Reference


### Syntax
```
volatility.exe -f <vmem file> --profile <profile> <plugin> [-D <outfile>] CONFIRM THIS SYNTAX!!!
```

### Important Commands

```
volatility -f .\0zapftis.vmem imageinfo
```
Get recommended profile

```
volatility -f .\0zapftis.vmem --profile "WinXPSP2x86" memdump -p 1640 -D .
```
Read previously run commands

```
volatility -f .\cridex.vmem --profile=WinXPSP2x86 cmdscan
```
Get console history

```
volatility -f .\0zapftis.vmem --profile=WinXPSP2x86 procdump -p 544 -D .
```
Search for a process by PID (-p option)

Note: this returns a executable that can be hashed and checked against other tools like virustotal

```
volatility -f .\0zapftis.vmem --profile=WinXPSP2x86 connscan
```
returns all network connections

```
.\volatility_2.6_win64_standalone.exe -f <file> --profile=<profile> driverscan
```
returns driver information
