# Forests, Trees, Domains
![forest-tree-domain](https://git.cybbh.space/os/public/-/raw/master/os/modules/014_windows_active_directory_enumeration/pages/ADimage1.png)
- *Domains*: Active Directory objects (users or devices) that all use the same database or are typically in the same location.
- *Trees*: Several Domains grouped together. Typically, has a primary domain controller for the entire tree.
- *Forests*: groups of trees connected together via trust relationships.

#Active Directory Enumeration

## Reading a SID
![Windows Diagram](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/media/security-identifier-architecture.png)

### S-1-5-21-1004336348-1177238915-682003330-1000

| S | 1 | 5 | 21-1004336348-1177238915-682003330 | 1000 |
| - | - | - | - | - |
| SID Identifier | Revision # | Authority Value | Sub-Authority Value (Domain Portion) | Relative Identifier (RID) |

- lists all powershell commands for active directory machines
```
Get-Command -Module activedirectory
```



# Enumerate Active Directory users and groups

## Get-ADGroupMember

```
Get-ADGroupMember [-Identity 'name'] [-Recursive]
```

## Get-ADUser

```
Get-ADUser [-Filter 'Name -like "*"']
```

### Examples

```
get-aduser -filter {Enabled -eq "FALSE"} -properties name, enabled
```
finds all disabled users

> [!NOTE] 

```
Enable-ADAccount -Identity <user>
```
can be used to enable any disabled accounts

```
get-aduser -filter *
```
get all users

```
search-adaccount -accountdisabled
```
An alternative method to finding disabled accounts

```
get-aduser -filter * -property EmailAddress | select EmailAddress | Where-Object {$_ -notmatch "mail.mil"}
```
Grabs all user's emails and filters out any that end with the domain "mail.mil"

```
get-aduser -filter 'name -like "Isiah"' -properties *
```
gets all properties for a user with a name similar to "Isiah"


# Edit Active Directory users and groups

## Enable-ADAccount

```
Enable-ADAccount -Identity <user>
```

## Set-AdAccountPassword

```
Set-AdAccountPassword -Identity guest -NewPassword (ConvertTo-SecureString -AsPlaintext -String "PassWord12345!!" -Force)
```

## 
