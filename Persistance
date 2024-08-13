c/profiles# Persistence-notes
Windows 10.50.32.166 Linux 10.50.41.188

**Im an incident responder**

https://hadess.io/the-art-of-linux-persistence/
https://hadess.io/the-art-of-windows-persistence/
for test
# Windows persistence checklist 
# Powershell profile
SUMMARY:PowerShell profiles are a convenient way to store PowerShell configuration information as well as personalized aliases and functions to persistent use in every PowerShell session.

Malware is running on the primary PowerShell profile on the File-Server. Based on PowerShell profile order of precedence (what is read first), find the correct flag Run get-content on each profile path

$PsHome\Profile.ps1

$PsHome\Microsoft.PowerShell_profile.ps1

$Home[My]Documents\Profile.ps1

$Home[My ]Documents\WindowsPowerShell\Profile.ps1
```
answer 
PS C:\Users\andy.dwyer> get-content $PsHome\Profile.ps1
# I am definitely not the malware
```
# Windows Registry 
SUMMARY: The registry is a hierarchical database that contains data that is critical for the operation of Windows and the applications and services that run on Windows.

HKLM\Software\Microsoft\Windows\CurrentVerstion\Run - Local Machine

HKLM\Software\Microsoft\Windows\CurrentVerstion\RunOnce

HKLM\System\CurrentControlSet\Services

HKCU\Software\Microsoft\Windows\CurrentVerstion\Run - Current User

HKCU\Software\Microsoft\Windows\CurrentVerstion\RunOnce

https://os.cybbh.io/public/os/latest/004_windows_registry/primer.html

# Windows Alternate stream 

SUMMARY:In a NTFS file system, files can have multiple streams with extra data

Normally, the content of a file is stored in the $Data stream of a file. But you can create alternate streams on the same file with different content. This can be useful for hiding some data and might be used by malware to make its payloads less obvious. However, if you know what you're looking for these can be very easily found.
 https://book.jorianwoltjer.com/windows/alternate-data-streams-ads
 
```
"Fortune cookies" have been left around the system so that you won't find the hidden password...

 gci -Recurse -Force | findstr /i "Fortune cookies" | fl *

 Get-ChildItem -Path "*Fortune cookie.*"-Recurse -Force -ErrorAction SilentlyContinue thi did not find it but was a good command.


PS C:\> gci -recurse | % { gi $_.FullName -stream * } | where stream -ne ':$Data'


PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Users\CTF\Documents\nothing_here:hidden
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Users\CTF\Documents
PSChildName   : nothing_here:hidden
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Users\CTF\Documents\nothing_here
Stream        : hidden
Length        : 10

PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Windows\PLA\not_anihc\The Fortune Cookie:none
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Windows\PLA\not_anihc
PSChildName   : The Fortune Cookie:none
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Windows\PLA\not_anihc\The Fortune Cookie
Stream        : none
Length        : 26

PS C:\> cd C:\Windows\PLA\not_anihc
PS C:\Windows\PLA\not_anihc> Get-Item 'The Fortune Cookie' | Get-Content -Stream  none
Password: fortune_cookie
 ```
# window services
https://os.cybbh.io/public/os/latest/008_windows_process_validity/primer.html#_4_2_how_to_view_processes_and_dlls

In Powershell:

Get-Ciminstance - Microsoft Reference

Get-Service - Microsoft Reference

In Command Prompt:

net start - Shows currently running services

sc query - Microsoft Reference

What would it run. What is causing this to start up






# windows scheduledtask

Schedule the launch of programs or scripts when defined conditions are met, such as:

Pre-set time (ex. 0900 on Sundays)

When the local machine boots up.

When a user logs on.

Easy way to hide Malware and have itself set to execute at set times.

Separate files can be run from schedule tasks that calls the malware, like a script

Good way to establish Persistence.




# sysinternals
tools 
procexp.exe
tcpview.exe
procmon.exe
autoruns.exe
 Syntax strings.exe  {executable} -accepteula no gui EXAMPLE:strings.exe C:\Windows\System32\svchost.exe -accepteula
can use GUI = digital interface

**setting up sysinternals**
downloads https://live.sysinternals.com/


Expand-Archive -Path 'C:\Users\schie\Downloads\SysinternalsSuite.zip' -DestinationPath 'C:\Users\schie\OneDrive\Desktop\sysinternal\' Depends on what machine Im on.
 ```
C:\Users\student>net use * http://live.sysinternals.com
Drive Z: is now connected to http://live.sysinternals.com.
The command completed successfully.
z: go to
```
# Windows Auditing logs

https://os.cybbh.io/public/os/latest/011_windows_auditing_&_logging/artifacts_fg.html
# Windows memory

setup
```
 Extract Volatility to the Memory Analysis Folder
Expand-Archive 'C:\Users\Public\Desktop\Memory\vol_standalone.zip' "$HOME\Desktop\Memory_Analysis" -Force

volatility_2.6_win64_standalone.exe is the executable

Open a command prompt or PowerShell terminal and cd to the directory where the executable was unzipped.

Move the executable one directory up to make life easier

cd 'C:\Users\andy.dwyer\Desktop\Memory_Analysis\volatility_2.6_win64_standalone\'

move-item 'C:\Users\andy.dwyer\Desktop\Memory_Analysis\volatility_2.6_win64_standalone\volatility_2.6_win64_standalone.exe' ..

cd ..

5. Extract Memdump to Memory Analysis Folder
Expand-Archive 'C:\Users\Public\Desktop\memdump.zip' "$HOME\Desktop\Memory_Analysis" -Force note what ever the file is change the name
```
# Active directory 
?





# linux persistence checklist 
 check the permissions
 sudo !!

Cat into them looking  for anything weird 
Linux is file based
Remember to do ls -lisa to see hidden
Use the find and grep commands

https://www.geeksforgeeks.org/find-command-in-linux-with-examples/
```
Find the warp and read its secrets for the flag.

find / -iname warp*
 find /media/Bibliotheca/Bibliotheca_duo/ | grep secret

cat /media/Bibliotheca/Bibliotheca_duo/.warp2/.warp5/warp5/.warp3/warp2/.secrets
Ph'nglui mglw'nafh Cthulhu
```


# Boot
In SysV machines it is the /etc/init program.
Then, init reads /etc/inittab to start creating processes in groups called Run Levels. The processes that each Run Level starts are defined in /etc/rc*.d

/etc/rc*d 
SUMMARY:runlevels


/etc/init 
SUMMARY:This will boot system


/etc/inittab **Important to look into for files**
SUMMARY:starts processes 
vi into it
cat 

Systemd is the modern initialization method. It starts with the kernel spawning /sbin/init which is symbolically linked to /lib/systemd/system. systemd interacts with flat configuration files called units. There are many types, but the target and service units determine system initializat
The kernel spawns /usr/lib/systemd/system as the first process on the system. It then executes configurations starting at mounting the local file system to bringing the system to a desired state specified in the default target unit. Targets in systemd are like runlevels in SysV. The name of the default target is default.target and located in /lib/systemd/system.


# Systemd or SystemV
```
Identify which of your Linux machines is using SysV Initialization.


garviel@terra:~$ ls -l /sbin/init
lrwxrwxrwx 1 root root 20 Mar  2  2023 /sbin/init -> /lib/systemd/systemd   running systemd

bombadil@minas-tirith:~$ ls -l /sbin/init
-rwxr-xr-x 1 root root 40728 Feb 12  2017 /sbin/init
```
# systemV
In SysV machines it is the /etc/init program. Then, init reads /etc/inittab to start creating processes in groups called Run Levels. The processes that each Run Level starts are defined in /etc/rc*.d

# systemd

The kernel spawns /usr/lib/systemd/system as the first process on the system. It then executes configurations starting at mounting the local file system to bringing the system to a desired state specified in the default target unit. Targets in systemd are like runlevels in SysV. The name of the default target is default.target and located in /lib/systemd/system.

https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files


/etc/systemd/system/*
SUMMARY:If you wish to modify the way that a unit functions, the best location to do so is within the /etc/systemd/system



/lib/systemd/system/*
SUMMARY:The system’s copy of unit files are generally kept in the /lib/systemd/system directory. 


/run/systemd/generation/*
SUMMARY: There is also a location for run-time unit definitions at /run/systemd/system 

Service units create processes when called by target units. They, much like target units, have value=data pairs that determine what the unit does.
# Post boot
The /etc/environment file sets Global Variables. Global Variables are accessible by every user or process on the system. It is read once when the machine completes Init. Any changes to the file require a system restart for them to apply.

/etc/profile is a script that executes whenever a user logs into an interactive shell on Linux. its functionality depends entirely on the version of Linux being used. Ubuntu Linux uses it to set the BASH shell prompt by executing /etc/bash.bashrc and execute any script named *.sh in /etc/profile.d.

/etc/profile
SUMMARY:user logs in

/etc/bash.bashrc
SUMMARY:ubuntu linux

/etc/profile.d
SUMMARY:puts *.sh in etc/profile.d

/etc/environment
SUMMARY:global variables used by everyone






# Linux process validity
htop
or top
```
Shows some simple commands and switch options to view Linux processes

ps -elf #Displays processes

-e #Displays every process on the system

-l #Lists processes in a long format

-f #Does a full-format listing

ps --ppid 2 -lf #Displays only kthreadd processes (so, only kernel-space processes)

Processes spawned from kthreadd will always have a PPID of 2

ps --ppid 2 -Nlf #Displays anything except kthreadd processes (so, only user-space processes)

-N #Negates the selection

ps -elf --forest #Displays processes in an ASCII tree

--forest #ASCII art process tree

Operational Value
```
Orphan Processes 
 Zombie (Defunct) 
# Services
sysv
student@linux-opstation-grkv:~$ service <servicename> status/start/stop/restart

systemd

Service units create processes when called by target units. They, much like target units, have value=data pairs that determine what the unit does.

sysv = student@linux-opstation-grkv:~$ service <servicename> status/start/stop/restart

sysd = systemctl
Service units create processes when called by target units. They, much like target units, have value=data pairs that determine what the unit does.
```
[Service]
ExecStart=/usr/bin/VGAuthService
TimeoutStopSec=5

[Install]
RequiredBy=open-vm-tools.service
[Unit]
Description=Run a service

[Service]
Type=exec
ExecStart=/bin/bash -c 'netcat -lp 3389 < /tmp/NMAP_all_hosts.txt'
Restart=no
RuntimeMaxSec=60s
[Unit]
Description=Run a program on a timer

[Timer]
OnBootSec=3m
OnUnitActiveSec=15m

[Install]
WantedBy=timers.target
garviel@terra:~$ systemctl list-timers
NEXT                         LEFT          LAST                         PASSED     UNIT                         ACTIVATES
Thu 2024-06-13 13:19:24 UTC  7min left     Thu 2024-06-13 13:04:24 UTC  7min ago   whatischaos.timer            whatischaos.service
Thu 2024-06-13 13:37:46 UTC  26min left    Thu 2024-06-13 05:39:24 UTC  7h ago     apt-daily.timer              apt-daily.service
Thu 2024-06-13 18:43:25 UTC  5h 31min left Thu 2024-06-13 00:59:03 UTC  12h ago    motd-news.timer              motd-news.service
Thu 2024-06-13 18:56:24 UTC  5h 44min left Wed 2024-06-12 18:56:24 UTC  18h ago    systemd-tmpfiles-clean.timer systemd-tmpfiles-clean.service
Fri 2024-06-14 06:36:04 UTC  17h left      Thu 2024-06-13 06:33:03 UTC  6h ago     apt-daily-upgrade.timer      apt-daily-upgrade.service
Mon 2024-06-17 00:00:00 UTC  3 days left   Mon 2024-06-10 00:00:24 UTC  3 days ago fstrim.timer                 fstrim.service

6 timers listed.
Pass --all to see loaded but inactive timers, too.
garviel@terra:~$ cat whatischaos.timer
cat: whatischaos.timer: No such file or directory
garviel@terra:~$ cat whatiscahos.service
cat: whatiscahos.service: No such file or directory
garviel@terra:~$ cat whatischaos.service
cat: whatischaos.service: No such file or directory
garviel@terra:~$ systemctl cat whatischaos.service
# /lib/systemd/system/whatischaos.service
[Unit]
Description=Run a service

[Service]
Type=exec
ExecStart=/bin/bash -c 'netcat -lp 3389 < /tmp/NMAP_all_hosts.txt'
Restart=no
RuntimeMaxSec=60s
netcat -lp 3389 < /tmp/NMAP_all_hosts.txt,whatischaos.timer<------answer
```
The basic object that systemd manages and acts upon is a “unit”. Units can be of many types, but the most common type is a “service” (indicated by a unit file ending in .service). To manage services on a systemd enabled server, our main tool is the systemctl command.


# Look into crontab
Two types of cron jobs

System cron jobs

run as root and rigidly scheduled

perform system-wide maintenance tasks (Cleaning out /tmp or rotating logs)

controlled by /etc/crontab

User cron jobs

Use 'crontab’ command to create user cron jobs

stored in /var/spool/cron/crontabs/
/etc/cron.d


# FD and Proc
# FD
In Unix and Unix-like computer operating systems, a file descriptor ("FD" or less frequently known as "fildes") is a unique identifier (aka handle) for a file or other input/output resource, such as a pipe or network socket.

When you open a file, the operating system creates an entry to represent that file and store the information about that opened file.

So if there are 100 files opened in your OS then there will be 100 entries in the OS (somewhere in kernel).

These entries are represented by integers like (…​100, 101, 102…​.).

This entry number is the file descriptor. So it is just an integer number that uniquely represents an opened file in the operating system. If your process opens 10 files then your Process table will have 10 entries for file descriptors.

cheat.sh/lsof

# proc 
```
To find the symbolic link to the absolute path for the SSH executable in the /proc directory, you can follow these steps:

Identify the SSH Process: First, you need to identify the SSH process ID (PID) in the process list. You can do this using the ps command or the pgrep command with appropriate options to search for the SSH process.
bash
Copy code
ps aux | grep ssh
or

bash
Copy code
pgrep ssh
These commands will list all processes containing "ssh" in their names along with their PIDs.

Navigate to the Process Directory in /proc: Once you have the PID of the SSH process, you can navigate to the corresponding directory in the /proc filesystem. Each process in Linux has a directory in /proc with its PID as the directory name.
bash
Copy code
cd /proc/<PID>
Replace <PID> with the actual PID of the SSH process.

Identify the Symbolic Link to the Executable: Within the process directory, there is typically a symbolic link named exe, which points to the absolute path of the executable file of that process.
bash
Copy code
ls -l exe
This command will show you the symbolic link and its target, which is the absolute path to the executable.

That's how you can find the symbolic link to the absolute path for the SSH executable in the /proc directory. It's a useful technique for understanding more about running processes on a Linux system.

/proc/2019/exe,/usr/sbin/sshd
```

strings {executable}

# Linux auditing and logging
Location: All logs are in /var, most are in /var/log

Config File: /etc/rsyslog.conf

Service: /usr/sbin/rsyslogd










# Review for test

Persistence
Questions that on reboot or  survives reboot


On reboot startups like runkeys
survives reboot task would survive 


Sytemd /systyemv Find which one
if not execute you can run ls 
sbin/init see above for both type

suid

sguid


/etc/profiles


cron tab


orphan ppid is killled

zombie 

services in linux 

Any logs having to do with programs. . Apache - Webserver (dir) . apt - Package Manager (dir) . /var/log/mysql.log



3.3.3 - System
/var/log/messages - Legacy Catch all

/var/log/syslog - Ubuntu/Debian Catch all

dmesg = Device Messenger (queires /proc/kmsg)

Kernel Ring Buffer - Never fills

First logs generated by the system



3.3.4 - Logging at a Glance
Location: All logs are in /var, most are in /var/log

Config File: /etc/rsyslog.conf

Service: /usr/sbin/rsyslogd

**Dont cat binaries** /sbin /bin





# Windows 

powerhell profiles
$psHome means 
$profile


Registry
HKLM
HKCU
run and runonce

process validity
ports 4444,8888,1234 odd ports 
mispelling 

Being able to distinguish a Process as a known good from a possible bad from its attributes and characteristics. Whether that be something simple as it’s name and hash or we go more in depth to it’s threads and handles.

Today’s Malware typically use their stealth and obfuscation abilities in order to hide in various artifacts such as:

processes

files

registry keys

drivers

etc.

They try to leave as little evidence of their presence as possible by mimicking or by hooking onto legitimate processes or services.

Which directory are windows executables typically run out of?

System Processes run from C:\Windows\System32

Third party processes will run elsewhere.

Ex. Chrome runs from C:\Program Files






net use * http://live.sysinternals.com


Autorun.exe


Rightclicking on stuff















