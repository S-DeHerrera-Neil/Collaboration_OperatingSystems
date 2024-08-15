# Downloading Sysinternals

## Recommended Method (download and unzip)

- Step 1: downloading sysinternals.zip
  - `Invoke-WebRequest "https://download.sysinternals.com/files/SysinternalsSuite.zip"` (Powershell)
  - Or enter the url in a webbrowser and the file will be downloaded automatically
- Step 1.5: Moving zipfile to another machine
  - Moving the zipfile to another machine: `scp SysinternalsSuite.zip 10.X.X.X:/Users/<user>/AppData/Local/Microsoft/WindowsApps`
  - Grabbing the zipfile from another machine: `scp 10.X.X.X:/Home/<user>/Downloads/SysinternalsSuite.zip /Users/<user>/AppData/Local/Microsoft/WindowsApps`
  - Upload via MobaXTerm (open a ssh session to the target machine and use the green up arrow to upload a file)
- Step 2: File Placement
  - Ideally the file should be placed in `C:\Users\<user>\AppData\Local\Microsoft\WindowsApps` (this means that the executables can be run from anywhere)
- Step 2: unpacking zipfile
  - `Expand-Archive SysinternalsSuite.zip .` (Powershell)

## Alternative Method (share drive)

```

```
