# Lab 05: Spiceworks Finance Shared Folder Ticket

## Objective

Resolve a help desk ticket from a Finance employee who cannot access the department’s shared folder. This lab demonstrates ticket management, Active Directory group verification, SMB share configuration, NTFS permissions, troubleshooting, testing, and documentation.

## Lab Environment

* Oracle VirtualBox
* Windows Server 2025: `DC01`
* Windows 11 workstation: `PC01`
* Active Directory domain: `LAB.local`
* User account: `LAB\jwhite`
* Security group: `LAB\Finance`
* Ticketing platform: Spiceworks Cloud Help Desk

## Ticket Summary

James White from the Finance department reported that he could not access the following network location:

`\\DC01\Finance`

The issue prevented him from accessing files needed for his daily work.

## Troubleshooting Process

1. Confirmed that the user was signed into PC01 as `LAB\jwhite`.
2. Verified network connectivity between PC01 and DC01.
3. Confirmed that DC01 resolved to `192.168.56.12`.
4. Used `net view \\DC01` and discovered that the Finance share did not exist.
5. Verified that `LAB\jwhite` was a member of the `LAB\Finance` security group.
6. Created the folder `C:\Shares\Finance` on DC01.
7. Shared the folder as `\\DC01\Finance`.
8. Granted the `LAB\Finance` group Change and Read share permissions.
9. Granted the `LAB\Finance` group Modify NTFS permissions.
10. Verified both permission layers with PowerShell and `icacls`.
11. Cleared the existing SMB connection on PC01.
12. Retested access and successfully created and saved a test file.

## Commands Used

```cmd
ping DC01
net view \\DC01
whoami
whoami /groups | findstr /i "Finance"
net use * /delete /y
```

```powershell
Get-SmbShareAccess -Name Finance
icacls C:\Shares\Finance
```

## Root Cause

The Finance shared folder had not been created or published as an SMB share on DC01. After the share was created, PC01 also retained an older SMB connection that needed to be cleared before the updated permissions took effect.

## Resolution

Created and shared the Finance folder on DC01, assigned the Finance security group the appropriate share and NTFS permissions, cleared the cached SMB connection, and confirmed read/write access from PC01.

## Security Considerations

Access was assigned to the Finance security group instead of directly to an individual user. This follows role-based access control and least-privilege principles while making access easier to manage.

## Skills Demonstrated

* Spiceworks ticket management
* Active Directory group verification
* Windows file sharing
* Share and NTFS permission configuration
* SMB troubleshooting
* PowerShell permission verification
* End-user communication
* Ticket documentation and closure

## Result

The user successfully accessed `\\DC01\Finance` from PC01 and created a test file. The resolution was documented in Spiceworks, communicated to the user, and the ticket was closed.
