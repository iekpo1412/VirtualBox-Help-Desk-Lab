# Lab 02 - Windows Permissions and UAC

## Objective

Simulate a Tier 1 Help Desk scenario involving a standard user who requires an approved application that needs administrative privileges to install.

The goal was to understand Windows privilege elevation, User Account Control (UAC), standard vs. administrator accounts, and the principle of least privilege.

## Environment

- Oracle VirtualBox
- Windows virtual machine
- Standard local user (`mreed`)
- Separate local administrator account
- Windows Command Prompt
- User Account Control (UAC)

## Ticket Scenario

**User:** Marcus Reed  
**Username:** mreed  
**Department:** Accounting

The user reported that they needed to install an application for work, but Windows requested an administrator username and password.

## Troubleshooting Process

1. Identified which application the employee needed.
2. Determined whether the application was approved for company use.
3. Verified that Tier 1 Help Desk was authorized to perform the installation.
4. Kept the employee logged into their standard Windows account.
5. Launched the approved application installer.
6. Used authorized administrator credentials when UAC requested elevation.
7. Performed the administrative action without permanently changing the employee's account privileges.
8. Verified the application installed successfully.
9. Confirmed that the employee could launch and use the application.

## User and Workstation Verification

Used the following command to identify the user context:

`whoami`

Used the following command to identify the workstation:

`hostname`

This demonstrated the difference between identifying the user account currently running a process and identifying the computer being supported.

## Root Cause

The employee was using a standard Windows account and therefore could not perform an administrative installation without authorized elevation.

This was expected security behavior rather than a Windows malfunction.

## Resolution

Verified that the requested software was approved and used authorized administrator credentials to elevate the installation through UAC.

The employee remained a standard user after the installation.

## Security Concepts

### Least Privilege

Employees should receive only the permissions required to perform their job responsibilities.

Giving users permanent administrator privileges unnecessarily increases security risk and allows system-level changes.

### Privilege Elevation

An individual process can be run with administrative privileges without permanently changing the employee's account to an administrator.

## What I Learned

- Difference between standard and administrator accounts
- How Windows UAC handles privilege elevation
- How to use `whoami` to identify the current user context
- How to use `hostname` to identify a workstation
- Why privilege elevation does not make the employee an administrator
- How least privilege applies to Help Desk support
- Why software authorization should be verified before installation
- Importance of verifying the resolution with the user

## Skills Practiced

- Windows 11
- User Account Control (UAC)
- Windows permissions
- Privilege elevation
- Command Prompt
- `whoami`
- `hostname`
- Least privilege
- Software support
- Tier 1 troubleshooting
- Technical documentation

## Screenshots

### UAC Administrator Prompt

![UAC Administrator Prompt](uac-admin-prompt.png)

Standard user encountering a UAC credential prompt when attempting an administrative action.

### Standard vs Administrator Context

![Standard vs Administrator](standard-vs-admin-whoami.png)

Comparison demonstrating the difference between the standard user's context and an elevated administrative process.

### User and Workstation Verification

![User and Workstation Verification](user-and-hostname-verification.png)

Using `whoami` and `hostname` to identify the current user and workstation.
