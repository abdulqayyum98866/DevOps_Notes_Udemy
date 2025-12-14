# 1 - Install PowerShell using WinGet

Source: https://learn.microsoft.com/en-us/powershell/scripting/install/install-powershell-on-windows?view=powershell-7.5

WinGet, the Windows Package Manager

## 1.2 - Install PowerShell using Microsoft Store
Open it.

## 1.3 - Check version
Type to know powershell version.

> $PSVersionTable

## 1.4 - Major monor package (Check version details)
> $PSVersionTable.psversion

## 1.5 - IMPORTANT CLARIFICATION (Very Important)
Use PowerShell 7+, not old Windows PowerShell

## 1.6 - Search for the latest version of PowerShell
> winget search --id Microsoft.PowerShell

## 1.7 - To determine whether PowerShell may be upgraded with WinGet, run the following command
> winget list --id Microsoft.PowerShell --upgrade-available

## 1.8 - If there is an available upgrade, the output indicates the latest available version. Use the following command to upgrade PowerShell using WinGet
> winget upgrade --id Microsoft.PowerShell

# 2 - Connect to AWS EC2 instance through powershell using SSH client
Source: 

## - PREREQUISITES (CHECK ONCE)

EC2 Public IP

Key file (.pem)

Username

Ubuntu → ubuntu

Amazon Linux → ec2-user

## 2.1 - Go to Folder Where .pem File Exists

PS C:\\> cd E:\\
PS E:\\> pwd

Path
----
E:

PS E:\\> cd .\Keys\
PS E:\\Keys> ls

Directory: E:\Keys

DevOps_ap_tokyo.pem





