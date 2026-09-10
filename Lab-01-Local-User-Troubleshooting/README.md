# Lab 01 - Local User Account Troubleshooting

## Objective

Simulate a Tier 1 Help Desk ticket involving an employee who is unable to sign in to their Windows workstation. Diagnose the issue, identify the root cause, restore access, and verify the resolution.

## Environment

- Oracle VirtualBox
- Windows virtual machine
- Local administrator account
- Standard local user account (`mreed`)

## Ticket Scenario

**User:** Marcus Reed  
**Username:** mreed  
**Department:** Accounting

The user reported being unable to sign in to their workstation despite previously being able to access the computer.

Windows displayed the following error:

> "The referenced account is currently disabled and may not be logged on to."

## Troubleshooting Process

1. Asked the user for the exact error message displayed during login.
2. Confirmed that the user had not recently changed their password.
3. Confirmed that Caps Lock was not interfering with password entry.
4. Identified the word "disabled" in the Windows error as an important troubleshooting clue.
5. Used Command Prompt with administrative privileges to inspect the local account:

   `net user mreed`

6. Discovered that the account status showed:

   `Account active: No`

7. Verified that the employee's account was supposed to be active.
8. Re-enabled the account:

   `net user mreed /active:yes`

9. Asked the user to attempt another login.
10. Confirmed that the user was able to successfully access their workstation.

## Root Cause

The employee's local Windows account had been disabled, preventing Windows authentication.

## Resolution

Re-enabled the local user account using an elevated Command Prompt and verified successful login with the user.

## What I Learned

- How to inspect local Windows user accounts from Command Prompt.
- How to enable and disable local Windows accounts.
- The difference between a local Windows account and a domain account.
- Why standard users and administrator accounts have different privileges.
- How error messages can provide clues during troubleshooting.
- The importance of verifying a fix before closing a ticket.

## Skills Practiced

- Windows user administration
- Command Prompt
- Local account management
- Authentication troubleshooting
- Access control
- Root cause analysis
- Tier 1 Help Desk troubleshooting
- Technical documentation

## Screenshots

Screenshots below demonstrate the VirtualBox lab environment and account verification.
