# Origional version of book notes. 

```
#Day 2
1. Windows Registry Introduction
The The Windows Registry is a central hierarchical database used in Windows to store information that is necessary to configure the system for one or more users, applications, and hardware devices.

Think of the Windows Registry like a huge Rolodex.

everything in Windows has a card/place with all of it’s information.

Includes location, information, settings, options, and other values for programs and hardware installed

Why is the registry important?

Anyone can hide all sorts of data including passwords, malicious code, and executable/binary files in the Registry.

They can effectively hide data in registry keys’ value entries.

By using different encoding techniques, they could obfuscate or hide data from forensic examiners.

It is important to know what right looks like and the places that are most likely to be compromised by a malicious actor.

Comparing the Registry in Windows to Linux
The registry in Windows is like a combination of multiple directories in Linux.

For example: Driver information is kept in the registry in Windows, but in /dev in Linux.

System configurations in Windows are in HKEY_LOCAL_MACHINE, but in /etc (and a few other directories) in Linux.
```
# Microsoft version 
```
Windows Registry Introduction
The Windows Registry is a central database in Windows that stores configuration information for users, applications, and hardware. Think of it as a huge Rolodex where everything in Windows has a card with its information, including locations, settings, options, and other values.

Importance of the Registry
  -Data Hiding: Passwords, malicious code, and executable files can be hidden in the Registry.
  -Obfuscation: Data can be encoded to hide it from forensic examiners.
  -Security: Knowing what is normal and identifying compromised areas is crucial.
Comparing Windows Registry to Linux
  -Driver Information: Stored in the Registry in Windows, but in /dev in Linux.
  -System Configurations: Found in HKEY_LOCAL_MACHINE in Windows, but in /etc and other directories in Linux.
```
# GPT
```
Windows Registry Overview
What is the Windows Registry?

  -The Windows Registry is a central database in Windows that stores settings and configurations for users, applications, and hardware.
  -You can think of it like a massive Rolodex, where every part of Windows has a "card" with all its information.

Why is the Registry Important?
  -It holds crucial data like locations, settings, and options for both software and hardware.
  -People can hide data, including passwords and malicious code, in the Registry. This can be done by:
    -Storing data in Registry keys’ value entries.
    -Using encoding techniques to hide information from forensic tools.

Windows Registry vs. Linux Directories
  -The Windows Registry is similar to several directories in Linux:
    -Driver Info: In Windows, it's stored in the Registry; in Linux, it's in /dev.
    -System Configurations: In Windows, it's under HKEY_LOCAL_MACHINE; in Linux, it’s spread across /etc and other directories.
```
