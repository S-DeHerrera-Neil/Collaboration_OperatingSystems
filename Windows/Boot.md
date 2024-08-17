# Boot Process Overview
![Windows Boot Full](http://1.bp.blogspot.com/-MaRtDTHH1Vo/UysJF8KXNbI/AAAAAAAAALo/D6Kt2f8Gpmo/s1600/Walkthrough_Diagram.jpg)

# Major steps:
 - Hardware Initialization(Part 1)
 - Loading the Boot Sector or Boot Manager(Part 2)
 - Loading the Operating System from the Boot Sector(Part 3)

Part 1. (Device Powers on -> firmware interfaces initializes {BIOS/UEFI})
   
   - BIOS: [BIOS](Additional_Information/BIOS.md)
   - UEFI: [UEFI](Additional_Information/UEFI.md)
After the BIOS or the UEFI have found their respective boot loaders they hand over their control of the boot process (End of Part 1)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Part 2. 
- ( BIOS -> MBR ) [MBR](Additional_Information/MBR.md)
- (UEFI -> UEFI Boot Managers) [UEFI_BootManagers](Additional_Information/UEFI_BootManagers.md)

### Tools:
 bcedit: [BCDEdit](Additional_Information/BDCEdit.md)
 Msinfo32.exe: [Msinfo32](Additional_Information/Msinfo32.md)
 

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

winload: [winload](Additional_Information/winload.md) 
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------   
## COMMANDS: 
- shows whether your machine is running BIOS or UEFI

      PS > findstr /C:"Detected boot environment" "C:\Windows\Panther\Setupact.log"
   
      PS > Get-Content C:\Windows\Panther\Setupact.log | Select-String "Detected boot environment"

- searches the output of BCDEdit for any lines that contain the text winload, regardless of case.

      > bcedit | findstr /i winload

 
# Loading the Boot Sector or Manager (Part 2)
  - After

# Loading the Operating System Kernel (Part 3)
 ### bootmgfw.efi(UEFI) reads a BCD(Boot Configuration Data) in the EFI system partition to load the winload.efi file

 ### bootmgr or NTDLR readds the file \Boot\BCD to locate winload.exe
    - Winresume.exe: readspreviously saved data from hiberfil.sys (hibernation mode) to restore a previous Windows instance
    - On UEFI, Winresume.exe is named winresume.efi located @ \Windows\System32\Boot   
  
 ### ntoskrnl.exe -> LogonUI.exe (End of Part 3)
--------------------------------------------------------------------------------------------------------------------------------------------------------------
 - Loading the Operating System Kernel
 - Initializing the Kernel
 - Starting Subsystems
 - Starting Session 0
 - Starting Session 1

# Starting Subsystems
![alt text](https://git.cybbh.space/os/public/-/raw/master/os/modules/006_windows_boot_process/pages/winboot1.png)

 

