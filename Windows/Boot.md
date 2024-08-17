# Boot Process Overview
![Windows Boot Full](http://1.bp.blogspot.com/-MaRtDTHH1Vo/UysJF8KXNbI/AAAAAAAAALo/D6Kt2f8Gpmo/s1600/Walkthrough_Diagram.jpg)

# Boot Process Broken into 3 Phases:
 - Phase 1.(Hardware Initialization)
 - Phase 2.(Loading the Boot Sector[BIOS]or Boot Managers[UEFI])
 - Phase 3.(Loading the Operating System from the Boot Sector)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#### Phase 1. (firmware interfaces initialize: BIOS or UEFI)
   - [BIOS](Additional_Information/BIOS.md)
   - [UEFI](Additional_Information/UEFI.md)
   - [bootmgr](Additional_Information/bootmgr.md) 
   - [Winresume](Additional_Information/winresume.md) 
 
 After either BIOS(.exe) or UEFI(.efi) initialize winload[.exe|.efi] (Phase 2. Begins)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#### Phase 2. (winload is initialized)
- ( BIOS -> MBR -> winload.exe) [MBR](Additional_Information/MBR.md)
- (UEFI -> UEFI -> winload.exe) [UEFI_BootManagers](Additional_Information/UEFI_BootManagers.md)
### Tools:
[BCDEdit](Additional_Information/BDCEdit.md)
[Msinfo32](Additional_Information/Msinfo32.md)
When winload is initialized it reads the BCD [BCDEdit](Additional_Information/BDCEdit.md).
Finds the kernel and starts it. (Phase 3. Begins)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#### Phase 3. (winload.exe starts the OS[ntoskernel.exe])
- [winload](Additional_Information/winload.md)
- [ntoskernel.exe](Additional_Information/ntoskernel.md)
 
 

### ntoskrnl.exe -> LogonUI.exe (End of Part 3)
(End of Phase 3 Start of [SubSystems](Additional_Information/SubSystems.md))
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------   
## COMMANDS: 
- shows whether your machine is running BIOS or UEFI

      PS > findstr /C:"Detected boot environment" "C:\Windows\Panther\Setupact.log"
   
      PS > Get-Content C:\Windows\Panther\Setupact.log | Select-String "Detected boot environment"

- searches the output of BCDEdit for any lines that contain the text winload, regardless of case.

      PS  > bcedit | findstr /i winload

 ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
