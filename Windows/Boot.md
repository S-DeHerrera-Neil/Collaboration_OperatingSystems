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
 
 #### After either BIOS(.exe) or UEFI(.efi) initialize winload[.exe|.efi] (Phase 2. Begins)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#### Phase 2. (winload is initialized)
- ( BIOS -> MBR -> winload.exe) [MBR](Additional_Information/MBR.md)
- (UEFI -> UEFI -> winload.exe) [UEFI_BootManagers](Additional_Information/UEFI_BootManagers.md)
### Tools:
[BCDEdit](Additional_Information/BDCEdit.md)
[Msinfo32](Additional_Information/Msinfo32.md)
#### When winload is initialized it reads the BCD [BCDEdit](Additional_Information/BDCEdit.md).
Finds the kernel and starts it. (Phase 3. Begins)
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#### Phase 3. (winload.exe starts the OS[ntoskernel.exe])
- [winload](Additional_Information/winload.md)
- [ntoskernel.exe](Additional_Information/ntoskernel.md)
 
 ### ntoskrnl.exe -> LogonUI.exe (End of Part 3)
#### (End of Phase 3 Start of [SubSystems](Additional_Information/SubSystems.md))
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------   
## COMMANDS: 
- shows whether your machine is running BIOS or UEFI

      findstr /C:"Detected boot environment" "C:\Windows\Panther\Setupact.log"
      
      Get-Content C:\Windows\Panther\Setupact.log | Select-String "Detected boot environment"

- searches the output of BCDEdit for any lines that contain the text winload, regardless of case.

      bcdedit | findstr /i winload
- Shows the Spooler Serivce using SC

      sc query spooler

- Shows the the Service Control Manager (SCM) registry key
 
      reg query HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services | findstr Spooler
- Shows the Contents of the Spooler Service Registry Key

      reg query HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler
- Shows Services
      
      C:\Windows> tasklist /svc
- BCDEdit help 
      
      C:\demo>bcdedit /?
- Backup & Restore Current BCD settings
      
      c:\demo>bcdedit /export C:\Lion_BCD
      c:\demo>bcdedit /import C:\Lion_BCD
- Modify Description of Current Boot loader

      c:\demo>bcdedit /set {<identifier>} description "Windows 7 - Lion Den" (1)
- Create New partition

      c:\demo>bcdedit /create {ntldr} /d "Windows XP Pro SP2 - Tiger Paw"
- -Specify the Partition

      c:\demo>bcdedit /set {ntldr} device partition=C:
- -Specify the Path to ntldr

      c:\demo>bcdedit /set {ntldr} path \ntldr
- -Specify the Display Order

      c:\demo>bcdedit /displayorder {ntldr} /addfirst
- Show the added Partition

      c:\demo>bcdedit
- Delete the Legacy Operating System ( /f = force)

      bcdedit /delete {ntldr} /f
- Add Safeboot Value

      bcdedit /deletevalue {current} safeboot (1)
      bcdedit /set {bootmgr} timeout 29 (2)
 --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 ### Locations of Interest
- /dev/sda1
- DISK 1 C:\
- \Boot\BCD
- C:\pagefile.sys

### DLLs of Interest
 
      - hal.dll




