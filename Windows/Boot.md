# Boot Process Overview
![Windows Boot Full](http://1.bp.blogspot.com/-MaRtDTHH1Vo/UysJF8KXNbI/AAAAAAAAALo/D6Kt2f8Gpmo/s1600/Walkthrough_Diagram.jpg)

# Boot Process Broken into 3 Phases:
 - Phase 1.(Hardware Initialization)
 - Phase 2.(Loading the Boot Sector[BIOS]or Boot Managers[UEFI])
 - Phase 3.(Loading the Operating System from the Boot Sector)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Phase 1. (firmware interfaces initializes {BIOS|UEFI})
   - [BIOS](Additional_Information/BIOS.md)
   - [UEFI](Additional_Information/UEFI.md)
   - [bootmgr](Additional_Information/bootmgr.md) 
   - [NTDLR](Additional_Information/NTDLR.md)
   - [Winresume](Additional_Information/winresume.md) 
 
 After either the [BIOS|UEFI] initialize, they use bootmgr or NTDLR to locate winload.exe.
 When they find them it starts Phase 2. (End of Phase 1)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# Phase 2. (firmware finds the bootloader)
- ( BIOS -> MBR -> winload.exe) [MBR](Additional_Information/MBR.md)
- (UEFI -> UEFI -> winload.exe) [UEFI_BootManagers](Additional_Information/UEFI_BootManagers.md)
### Tools:
 - bcedit: [BCDEdit](Additional_Information/BDCEdit.md)
 - Msinfo32.exe: [Msinfo32](Additional_Information/Msinfo32.md)
When the [BIOS|UEFI] find their bootloaders they start them.
This starts Phase 3. (End of Phase 2)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Phase 3. (winload.exe starts the OS[ntoskernel.exe])
- [winload](Additional_Information/winload.md)
- [ntoskernel.exe](Additional_Information/ntoskernel.md)
 
 ### bootmgfw.efi(UEFI) reads a BCD(Boot Configuration Data) in the EFI system partition to load the winload.efi file

### ntoskrnl.exe -> LogonUI.exe (End of Part 3)
(End of Phase 3 Start of [SubSystems](Additional_Information/SubSystems.md))
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------   
## COMMANDS: 
- shows whether your machine is running BIOS or UEFI

      PS > findstr /C:"Detected boot environment" "C:\Windows\Panther\Setupact.log"
   
      PS > Get-Content C:\Windows\Panther\Setupact.log | Select-String "Detected boot environment"

- searches the output of BCDEdit for any lines that contain the text winload, regardless of case.

      > bcedit | findstr /i winload

 ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 - Loading the Operating System Kernel
 - Initializing the Kernel
 - Starting Subsystems
 - Starting Session 0
 - Starting Session 1

# Starting Subsystems
![alt text](https://git.cybbh.space/os/public/-/raw/master/os/modules/006_windows_boot_process/pages/winboot1.png)

 

