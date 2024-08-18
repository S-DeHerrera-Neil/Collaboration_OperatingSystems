# Start of Subsystems
![alt text](https://git.cybbh.space/os/public/-/raw/master/os/modules/006_windows_boot_process/pages/winboot1.png)

 Ntoskrnl.exe start SYSTEM
 SYSTEM starts Smss.exe
 Smss.exe starts Csrss.exe
 
 Smss.exe has Estabishes 2 Sessions
 - Session 0
    - Smss.exe(0) starts Csrss.exe & Wininit.exe
        - Csrss.exe...
        - Wininit.exe starts services & lsass.exe
            - Svchost.exe(1)
            - Svchost.exe(2)
            - SvcHost.exe(3).... 
 - Session 1
    - Smss.exe(1) starts Csrss.exe & Winlogon.exe
    - Csrss.exe...
        - Winlogon.exe Starts LogonUI.exe & UserInint.exe
            - LogonUI.exe...
            - Userinit.exe starts Explorer.exe
                - Explorer.exe is the GUI that the Authenticated User interacts with. 

