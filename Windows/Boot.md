1. Boot Process Overview
# Entire Boot Process
![Windows Boot Full](http://1.bp.blogspot.com/-MaRtDTHH1Vo/UysJF8KXNbI/AAAAAAAAALo/D6Kt2f8Gpmo/s1600/Walkthrough_Diagram.jpg)

There are three major steps:
 - Hardware Initialization
 - Loading the Boot Sector or Boot Manager
 - Loading the Operating System from the Boot Sector

2. BIOS vs UEFI

 - BIOS (supports up to 2 Terabytes)
   - MBR (Master Boot Record): contains Disk Partitions
        ### The MBR is 512 bytes, separated into 6 parts:
         - Bootstrap Code (446 bytes)
         - Partition entry 1 (16 bytes)
         - Partition entry 2 (16 bytes)
         - Partition entry 3 (16 bytes)
         - Partition entry 4 (16 bytes)
         - Boot Signature (2 bytes)
               - The Partition code that starts the first stage of loading an Operating System is referred to as the "Boot Loader"    

 - UEFI (supports up to 9 Zettabytes)
   - UEFI Boot Manager: Unlike the BIOS (that reads the MBR), the UEFI reads an EFI Partition.
        - The EFI Partition contains UEFI Boot Managers [Windows bootmgfw.efi or Windows Boot Manager]

# How to tell if your machine is running BIOS or UEFI

   '''
findstr /C:"Detected boot environment" "C:\Windows\Panther\Setupact.log"
Get-Content C:\Windows\Panther\Setupact.log | Select-String "Detected boot environment"
'''
# bcedit
'''
bcedit | findstr /i winload
'''
# Checking the GUI
'''
Msinfo32.exe
'''
2. Windows System Initialization

# ntoskrnl.exe -> LogonUI.exe (In 5 Parts)
 - Loading the Operating System Kernel(Part 1)
 - Initializing the Kernel(Part 2)
 - Starting Subsystems(Part 3)
 - Starting Session 0(Part 4)
 - Starting Session 1( Part 5)

# Loading the Operating System Kernel(Part 1)
 ## bootmgfw.efi(UEFI) reads a BCD(Boot Configuration Data) in the EFI system partion to load the winload.efi file
 ## bootmgr or NTDLR readds the file \Boot\BCD to locate winload.exe
  - winload programs: load basic drivers and start the next part of the Windows Boot Process- loading the Kernel(ntoskrnl.exe)
   - winload.exe: load essential drivers required to read data from the disk, loads ntoskrnl(and dependencies)
   - Winresume.exe: readspreviously saved data from hiberfil.sys (hibernation mode) to restore a previous Windows instance
    - On UEFI, Winresume.exe is named winresume.efi located @ \Windows\System32\Boot   
  

3. Starting Subsystems
 
# User Subsystems
![alt text](https://git.cybbh.space/os/public/-/raw/master/os/modules/006_windows_boot_process/pages/winboot1.png)

 
