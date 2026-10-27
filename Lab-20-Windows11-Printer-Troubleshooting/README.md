# Lab 20 — Windows 11 Printer Troubleshooting

## Objective
Investigate a simulated Windows printing problem using Print Spooler service controls, PowerShell printer/queue diagnostics, driver inspection, and Windows Event Viewer. Validate that Microsoft Print to PDF works after troubleshooting.

## Environment
- Windows 11 virtual machine, domain test user account
- Elevated Windows PowerShell for administrative operations
- Microsoft Print to PDF (no physical printer required)

## Scenario
A user reports that printing is not working. Investigate service status, installed printer, print queue, driver availability, and logging. Simulate a service interruption and validate functionality.

## Procedure and evidence
1. Inspected Print Spooler in `services.msc`: service initially **Running**, startup **Automatic** (`01-spooler-running.png`).
2. Verified the print queue initially showed **No print jobs** (`02-empty-print-queue.png`).
3. Stopped the service with elevated PowerShell using `Stop-Service -Name Spooler`; confirmed **Stopped** with `Get-Service -Name Spooler` (`03-spooler-stopped-powershell.png`).
4. Attempted a test print from Notepad to Microsoft Print to PDF (`04-print-dialog-test.png`). The print dialog closed without a clearly observed error or saved file at that point.
5. Observed that Print Spooler later returned to **Running**, without an explicit manual start in the recorded steps. Root cause of restart was **not established** (`05-spooler-restarted-observation.png`).
6. Reviewed service Recovery settings: first and second failures set to restart service. These settings alone do **not** establish why a normally stopped service restarted (`06-spooler-recovery-settings.png`).
7. Used `Get-Printer | Format-Table Name, PrinterStatus, DriverName` to confirm Microsoft Print to PDF had status **Normal**; `Get-PrintJob -PrinterName "Microsoft Print to PDF"` returned no pending jobs (`07-printer-and-queue-diagnostics.png`).
8. Repeated the test print successfully and opened the generated PDF (confirmed during lab; output PDF not included in this package).
9. Navigated to Event Viewer > Applications and Services Logs > Microsoft > Windows > PrintService > Operational. The log was **Disabled** and enabling it reportedly returned a permissions error; VM later became unresponsive and was restarted. No PrintService event was collected (`08-printservice-operational-disabled.png`).
10. Listed installed drivers with `Get-PrinterDriver | Format-Table Name, Manufacturer, MajorVersion`, including Microsoft Print To PDF (MajorVersion 4) (`09-printer-driver-inspection.png`). MajorVersion here indicates driver model type, not a specific package release.
11. Confirmed final service state using `Get-Service -Name Spooler | Format-Table Name, Status, StartType`: **Running / Automatic** (`10-final-service-verification.png`).

## Commands used
```powershell
Stop-Service -Name Spooler
Get-Service -Name Spooler
Get-Printer | Format-Table Name, PrinterStatus, DriverName
Get-PrintJob -PrinterName "Microsoft Print to PDF"
Get-PrinterDriver | Format-Table Name, Manufacturer, MajorVersion
Get-Service -Name Spooler | Format-Table Name, Status, StartType
```

## Outcome
- Confirmed installed virtual printer and inspected the print queue and driver inventory.
- Simulated a Print Spooler interruption and verified the service was stopped.
- Successfully validated PDF printing after service returned to Running.
- Confirmed final healthy service configuration (Running, Automatic).

## Limitations / follow-up
- No physical/network printer or real driver failure was tested.
- No stuck print job was captured; the queue was empty when queried.
- Operational event logging could not be enabled in this session due to reported permission issues.
- The observed automatic service restart was not conclusively explained.

## Skills demonstrated
Windows 11 support · Print Spooler · Windows Services · PowerShell · Printer diagnostics · Print queue inspection · Driver inventory · Event Viewer · Administrative access troubleshooting · Technical documentation
