# Windows 11 STIG Implementation & Vulnerability Management

## Overview
This project focused on identifying and remediating Windows 11 DISA STIG findings using Tenable compliance scans and manual remediation techniques.

The objective was to improve system hardening, validate compliance findings, and strengthen the overall security posture through vulnerability remediation and rescanning.

---

## Technologies Used
- Tenable / Nessus
- Windows 11
- PowerShell
- Registry Editor
- DISA STIGs
- Vulnerability Management
- Compliance Auditing

---

## Skills Demonstrated
- Vulnerability Management
- Security Hardening
- Risk Prioritization
- STIG Compliance
- Registry-Based Remediation
- Security Documentation
- Compliance Validation
- PowerShell Remediation

---

## Example Finding

### WN11-AU-000500
**Requirement:**  
The Application event log size must meet Windows 11 STIG minimum requirements.

### Issue Identified
The initial configuration used a legacy Windows 10 registry value (`32768 KB`), which failed validation against the Windows 11 benchmark.

### Registry Path
```registry
HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\EventLog\Application
```

### Remediation
Updated the `MaxSize` registry value to meet Windows 11 STIG requirements.

### Validation
The system was rescanned after remediation to validate compliance.

---

## Outcome
This project provided hands-on experience with:
- vulnerability scanning
- STIG remediation
- Windows hardening
- compliance validation
- operational security workflows
