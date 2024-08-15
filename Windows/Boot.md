# Boot Process Overview
![Windows Boot Full](http://1.bp.blogspot.com/-MaRtDTHH1Vo/UysJF8KXNbI/AAAAAAAAALo/D6Kt2f8Gpmo/s1600/Walkthrough_Diagram.jpg)

# Major steps:
 - Hardware Initialization(Part 1)
 - Loading the Boot Sector or Boot Manager(Part 2)
 - Loading the Operating System from the Boot Sector(Part 3)


# Important Hardware that is part of the Hardware Initialization Phase(Part 1)
                                                             
                                                             BIOS vs UEFI
                                                             
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

## COMMAND(s): showing whether your machine is running BIOS or UEFI
   PS > findstr /C:"Detected boot environment" "C:\Windows\Panther\Setupact.log"
   
   PS > Get-Content C:\Windows\Panther\Setupact.log | Select-String "Detected boot environment"

### bcedit (BDCEdit.exe): a Command Line tool used to create new stores, modify existing stores, and add boot menu options.
    - BCD (Boot Configuration Files) provides a store that's used to describe boot applications and boot application settings
    - winload refers to the Windows Boot Loader executable (winload.exe), which is responsible for loading the operating system kernel and other critical  
     components during the boot process. This command can be useful for finding information related to the boot loader configuration, such as its path or 
     settings, within the BCD store.

## COMMAND: searches the output of BCDEdit for any lines that contain the text winload, regardless of case.
    bcedit | findstr /i winload

### Msinfo32.exe (System Information): a Built-In Windows Utility that provides comprehensive information about a Computer's Hardware, Software, and System Configuration.  


# Windows System Initialization

### ntoskrnl.exe -> LogonUI.exe (In 5 Parts)
 - Loading the Operating System Kernel(Part 1)
 - Initializing the Kernel(Part 2)
 - Starting Subsystems(Part 3)
 - Starting Session 0(Part 4)
 - Starting Session 1( Part 5)


## Loading the Operating System Kernel(Part 1)
 ### bootmgfw.efi(UEFI) reads a BCD(Boot Configuration Data) in the EFI system partion to load the winload.efi file

 ### bootmgr or NTDLR readds the file \Boot\BCD to locate winload.exe
  - winload programs: load basic drivers and start the next part of the Windows Boot Process- loading the Kernel(ntoskrnl.exe)
   - winload.exe: load essential drivers required to read data from the disk, loads ntoskrnl(and dependencies)
   - Winresume.exe: readspreviously saved data from hiberfil.sys (hibernation mode) to restore a previous Windows instance
    - On UEFI, Winresume.exe is named winresume.efi located @ \Windows\System32\Boot   
  

# Starting Subsystems
![alt text](https://git.cybbh.space/os/public/-/raw/master/os/modules/006_windows_boot_process/pages/winboot1.png)

 
