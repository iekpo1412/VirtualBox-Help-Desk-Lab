# Lab 03 - Windows Network Troubleshooting

## Objective

The goal of this lab was to practice Tier 1 Windows network troubleshooting using a Windows 11 VirtualBox workstation.

This lab focused on identifying and resolving problems involving:

- IPv4 configuration
- DHCP
- DNS
- Default gateway connectivity
- External network connectivity
- Name resolution
- Basic route testing

## Environment

- Windows 11 virtual machine
- VirtualBox
- Standard user account: `mreed`
- Internet-facing adapter: `Ethernet 2`
- VirtualBox NAT networking

## Commands Used

```cmd
ipconfig
ipconfig /all
ipconfig /release
ipconfig /renew
ping 10.0.3.2
ping 8.8.8.8
ping google.com
nslookup google.com
tracert 8.8.8.8
ncpa.cpl
