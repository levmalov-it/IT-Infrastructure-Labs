# Lab 12 — Windows DNS Troubleshooting and Resolution

## Objective
Diagnose and resolve a DNS resolution failure preventing Microsoft Outlook from loading in a Windows virtual machine.

## Lab Environment
- Windows client VM running in UTM on macOS
- UTM shared network (NAT)
- Previously configured Active Directory domain: corp.local
- Windows Server 2022 domain controller (powered off during testing)
- PowerShell and Windows networking utilities

## Problem Description
Outlook displayed ERR_NAME_NOT_RESOLVED and could not load its sign-in page. The Windows client could not resolve external hostnames using its configured DNS servers.

## Troubleshooting Steps

### 1. Test Default DNS
```powershell
nslookup outlook.office.com
```
Result: DNS request timed out.

### 2. Test Public DNS
```powershell
nslookup outlook.office.com 8.8.8.8
```
Result: Successful DNS resolution, confirming connectivity to Google's IPv4 DNS service.

### 3. Inspect DNS Configuration
```powershell
Get-DnsClientServerAddress
ipconfig /all
```
The client used UTM-provided DNS addresses, including 192.168.64.4 and an IPv6 DNS address.

### 4. Test UTM DNS
```powershell
nslookup outlook.office.com 192.168.64.4
```
Result: DNS request timed out.

### 5. Verify Gateway Connectivity
```powershell
ping 192.168.64.1
```
Result: Four replies received with 0% packet loss.

### 6. Test Active Directory Discovery
```powershell
nslookup corp.local
nltest /dsgetdc:corp.local
```
Result: Domain controller discovery failed with error 1355. The domain controller VM was powered off during testing.

### 7. Apply Temporary DNS Workaround
Configured public DNS resolvers for IPv4 and IPv6 using Set-DnsClientServerAddress. This was a temporary workaround for testing external connectivity, not a repair of the UTM DNS service.

### 8. Verify Resolution
```powershell
nslookup outlook.office.com
```
Result: Successful resolution using Google's IPv6 DNS server (2001:4860:4860::8888). Outlook subsequently loaded its account setup screen.

## Outcome
Restored external DNS resolution and removed the ERR_NAME_NOT_RESOLVED blocker in Outlook. Mailbox sign-in and email functionality were not tested.

## Key Skills Demonstrated
- Windows network troubleshooting
- DNS diagnosis and configuration
- IPv4 and IPv6
- PowerShell
- Active Directory connectivity troubleshooting
- Root-cause investigation and technical documentation

## Important Note
The public DNS configuration is temporary. Before resuming Active Directory labs, restore the appropriate internal DNS settings and verify domain controller connectivity.

## Screenshots
Screenshots documenting the initial error, DNS failures, network configuration, successful resolution, and Outlook recovery will be added to the screenshots directory.
