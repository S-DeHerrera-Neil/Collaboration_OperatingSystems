# Downloading Sysinternals

## Recommended Method (download and unzip)

- Step 1: downloading sysinternals.zip
  - CMD  
  ``` 
  Invoke-WebRequest "https://download.sysinternals.com/files/SysinternalsSuite.zip"
  ```
  (Powershell)
  - Or enter the url 
  ```
  https://download.sysinternals.com/files/SysinternalsSuite.zip
  ```
   into a web browser and the file will be downloaded automatically
- Step 1.5: Moving zipfile to another machine (if neccessary)
  - Moving the zipfile to another machine:
```
> scp <file_to_send> <remote_ip>:<where_to_send_file>
> scp SysinternalsSuite.zip 10.X.X.X:/Users/<user>/AppData/Local/Microsoft/WindowsApps
```
  - Grabbing the zipfile from another machine:
```
> scp <remote_ip>:<path_to_file> <where_to_send_file>
> scp 10.X.X.X:/Home/<user>/Downloads/SysinternalsSuite.zip /Users/<user>/AppData/Local/Microsoft/WindowsApps
```
  - Upload via MobaXTerm (open a ssh session to the target machine and use the green up arrow in the file manager window on the left to upload a file)
- Step 2: File Placement
  - Ideally the file should be placed in:
  ```
  C:\Users\<user>\AppData\Local\Microsoft\WindowsApps
  ```
   (this allows you to run these programs without being in this directory)
  - This can be done by running:
    ```
    move SysinternalsSuite.zip "C:\Users\<user>\AppData\Local\Microsoft\WindowsApps"
    ```
    (CMD and Powershell)
- Step 2: unpacking zipfile
  - (Powershell)
  ```
  Expand-Archive SysinternalsSuite.zip .
  ``` 
  - Or extract all via the file explorer gui

## Alternative Method (share drive)

- Step 1: Link sysinternals tool to drive
  - (cmd or powershell)
  ```
  net use * http://live.sysinternals.com 
  ```
- Step 2: change directory to Z drive to access and run programs
  - 
  ```
  cd Z:\
  ```
Note: this will not work if you are not in the Z drive or if the machine does not have access to the internet.

# Command Syntax

### Strings
grabs all valid ascii characters from a file and writes them to the console

```
Strings <infile> -accepteula
```
