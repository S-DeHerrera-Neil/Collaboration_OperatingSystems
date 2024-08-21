# Powershell Profiles

These save Powershell settings for users and systems and can be used to establish **persistence**

## Locations

### All Users, All Hosts
```
$PsHome\Profile.ps1
```
### All Users, Current Host
```
$PsHome\Microsoft.PowerShell_profile.ps1
$PsHome\Microsoft.PowerShellISE_profile.ps1 # For Powershell ISE
```
### Current Users, All Hosts
```
$Home\[My]Documents\Profile.ps1
```
### Current User, Current Host
```
$Home\[My ]Documents\WindowsPowerShell\Profile.ps1
$Home\[My]Documents\WindowsPowerShell\Microsoft.PowerShellISE_profile.ps1 # For Powershell ISE
```

## Enumerations

```
Test-Path -Path $profile.currentusercurrenthost
```
This tests whether the profile has been created or not


can replace with `currentUserAllHosts`, `AllUsersAllHosts`, or `AllUserscurrentHost`
