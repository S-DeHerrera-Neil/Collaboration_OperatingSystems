# Forests, Trees, Domains
![forest-tree-domain](https://git.cybbh.space/os/public/-/raw/master/os/modules/014_windows_active_directory_enumeration/pages/ADimage1.png)
- Domains
  - Active Directory objects (users or devices) that all use the same database or are typically in the same location.
- Trees
  - Several Domains grouped together. Typically, has a primary domain controller for the entire tree.
- Forests
  - Forests are groups of trees connected together via trust relationships.

# Active Directory Enumeration

```
Get-Command -Module activedirectory
```
lists all powershell commands for active directory machines


# Enumerate active-directory users and groups

## Get-ADGroupMember

```
Get-ADGroupMember [-Identity 'name'] [-Recursive]
```

## Get-ADUser

```
Get-ADUser [-Filter 'Name -like "*"']
```

### examples

```
get-aduser -filter {Enabled -eq "FALSE"} -properties name, enabled
```
finds all disabled users

Note: `Enable-ADAccount -Identity <user>` can be used to enable any disabled accounts

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
