# VM Range (VPN or local network access required)
![alt text](https://git.cybbh.space/os/public/-/raw/master/images/Range_Diagram3.PNG)

| Name | IP | User/Password | OS | GUI | Networking |
| - | - | - | - | - | - |
| Domain Controller | 10.X.0.1 | andy.dwyer : BurtMacklinFBI | Windows Server 2019 | Limited* | N |
| Admin-Server | 10.50.X.X | andy.dwyer : BurtMacklinFBI | Windows 10 Enterprise | Full | Y |
| File-Server | 10.X.0.3 | andy.dwyer : BurtMacklinFBI | Windows Server 2019 | Limited* | N |
| Workstation2 | 10.X.0.4 | andy.dwyer : BurtMacklinFBI | Windows 10 Enterprise | None | N |
| Workstation1 | 10.X.0.5 | student : password | Windows 10 Enterprise | Full | Y |
| Terra | 10.X.0.6 | garviel : luna | Linux Ubuntu | None | Y |
| Minas-Tirith | 10.X.0.7 | bombadil : jolly | Linux Debian | None | Y |

## Windows 
  - [File_Search](Windows/File_Search.md)
  - [Registry](Windows/Registry.md)
  - [Boot](Windows/Boot.md)
  - [Processes/Services](Windows/Processes_and_Services.md)
  - [Logging/Security](Windows/Logging_and_Security.md)
  - [Memory Analysis](Windows/Memory_Analysis.md)
  - [Sysinternals](Windows/Sysinternals.md)

## Linux
  - [File_Search](Linux/File_Search.md)
  - [Boot](Linux/Boot.md)
  - [Processes/Services](Linux/Processes_and_Services.md)
  - [Logging/Security](Linux/Logging_and_Security.md)

## Resources:
- [cybbh_handbook](https://os.cybbh.io/public/os/latest/index.html)
- [cybbh_setup_guide](https://cctc.cybbh.io/students/students/latest/Day_0_Setup.html)
- [VTA_Range](https://vta.cybbh.space/)
- [CTF (VPN or local network access required)](http://10.50.22.197:8000)


- [Persistance](Persistance.md)



\*
This machine does not have a full gui, open taskmgr.exe by entering `ctrl` + `shift` + `esc` then hitting "file" and "run new task". Run cmd.exe to open a commandline.
