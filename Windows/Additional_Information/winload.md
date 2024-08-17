# winload: refers to the Windows Boot Loader executable (winload.exe), which is responsible for loading the operating system kernel and other critical  
  components during the boot process. 
  This command can be useful for finding information related to the boot loader configuration, such as its path or 
  settings, within the BCD store.

    > bcedit | findstr /i winload

  - winload programs: load basic drivers and start the next part of the Windows Boot Process- loading the Kernel(ntoskrnl.exe)
  - winload.exe: load essential drivers required to read data from the disk, loads ntoskrnl(and dependencies)
