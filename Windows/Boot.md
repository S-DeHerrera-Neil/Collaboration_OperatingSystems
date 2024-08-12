# Entire Boot Process
### (Windows NT 6 Boot Process w/ system files)
![Windows Boot Full](http://1.bp.blogspot.com/-MaRtDTHH1Vo/UysJF8KXNbI/AAAAAAAAALo/D6Kt2f8Gpmo/s1600/Walkthrough_Diagram.jpg)

There are three major steps:
 - Hardware Initialization
 - Loading the Boot Sector or Boot Manager
 - Loading the Operating System from the Boot Sector

1. BIOS vs UEFI

 - BIOS (supports up to 2 Terabytes)
   - MBR (Master Boot Record): contains Disk Partitions
        - The MBR is 512 bytes, separated into 6 parts:
         - Bootstrap Code (446 bytes)
         - Partition entry 1 (16 bytes)
         - Partition entry 2 (16 bytes)
         - Partition entry 3 (16 bytes)
         - Partition entry 4 (16 bytes)
         - Boot Signature (2 bytes)
               - The Partition code that starts the first stage of loading an Operating System is referred to as the "Boot Loader"    

 - UEFI (supports up to 9 Zettabytes)
   - UEFI Boot Manager: Unlike the BIOS (that reads the MBR), the UEFI reads an EFI Partition.
        -

     
2. Windows System Initialization


3. Starting Subsystems
 
# User Subsystems
![alt text](https://git.cybbh.space/os/public/-/raw/master/os/modules/006_windows_boot_process/pages/winboot1.png)

 
