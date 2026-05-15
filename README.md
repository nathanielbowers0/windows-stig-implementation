# Windows 11 STIG Implementation & Vulnerability Management

## Overview
This project focused on identifying, validating, and remediating Windows 11 DISA STIG findings using Tenable compliance auditing, manual remediation techniques, and PowerShell automation.

The objective was to strengthen endpoint security posture, validate compliance findings, and demonstrate the full vulnerability management lifecycle from detection through remediation and compliance validation.

---

## Technologies Used
- Tenable / Nessus
- Windows 11
- PowerShell
- Windows Registry Editor
- DISA STIGs
- Vulnerability Management
- Compliance Auditing
- Security Hardening

---

## Skills Demonstrated
- Vulnerability Management
- Windows Security Hardening
- STIG Compliance Implementation
- Registry-Based Remediation
- PowerShell Scripting
- Compliance Validation
- Risk Prioritization
- Security Documentation
- Operational Security Workflows

---

# Example STIG Remediation

## WN11-AU-000500

### Requirement
The Windows Application Event Log size must be configured to `32768 KB` or greater to meet DISA STIG compliance requirements.

---

## Initial Manual Remediation Validation

The STIG was initially remediated manually through Windows Group Policy and registry configuration changes before PowerShell automation was developed.

### Registry Path

```registry
HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\EventLog\Application
```

### Registry Configuration
- Registry Value: `MaxSize`
- Value Type: `REG_DWORD`
- Required Value: `32768 KB`

### Initial Compliance Validation

A Tenable rescan confirmed successful compliance validation after the manual remediation was applied.

<img width="1101" height="300" alt="initial-manual-remediation-pass" src="https://github.com/user-attachments/assets/c1711b7d-6a1b-482f-b25a-86d9c9d8649b" />

---

## Failure Validation

The policy configuration was reverted to validate that the system would properly fail compliance rescanning prior to PowerShell automation development.

### Group Policy Reset

<img width="1154" height="718" alt="Policy Reset" src="https://github.com/user-attachments/assets/dfa51736-44bd-49a8-8714-7c13b5fd0e27" />

### Failed Compliance Rescan

<img width="1454" height="372" alt="wn11-au-000500-failure-validation" src="https://github.com/user-attachments/assets/513ffbd4-fda6-42d7-8906-3834c51860f2" />

---

## Registry Validation

The Windows registry configuration was manually reviewed to validate the Application Event Log remediation target.

### Registry Path

```registry
HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\EventLog\Application
```

### Registry Validation Screenshot

<img width="1146" height="586" alt="registry-remediation" src="https://github.com/user-attachments/assets/6fdf7bd1-fe51-4828-b98d-851809c1ae2d" />

---

## PowerShell Remediation

A PowerShell remediation script was developed to automate the STIG implementation process and standardize future remediation workflows.

```powershell
# WN11-AU-000500 Remediation
# Configure Application Event Log Size to 32768 KB

$registryPath = "HKLM:\SOFTWARE\Policies\Microsoft\Windows\EventLog\Application"
$valueName = "MaxSize"
$valueData = 32768

# Create registry path if it does not exist
if (!(Test-Path $registryPath)) {
    New-Item -Path $registryPath -Force
}

# Configure registry value
Set-ItemProperty -Path $registryPath -Name $valueName -Value $valueData -Type DWord

Write-Host "WN11-AU-000500 remediation applied successfully."
```

### PowerShell Script Execution

<img width="1128" height="622" alt="wn11-au-000500-powershell-remediation" src="https://github.com/user-attachments/assets/94df9120-56e5-404d-8bed-b84a9f9c1673" />

---

## Final Compliance Validation

After PowerShell remediation, the system was rescanned using Tenable to validate successful DISA STIG compliance.

<img width="1091" height="336" alt="wn11-au-000500-passed-scan" src="https://github.com/user-attachments/assets/8b15f2e6-553f-44eb-9a47-dd3d7f4e6244" />

---

# Outcome

This project provided hands-on experience with:

- DISA STIG remediation workflows
- vulnerability scanning and validation
- Windows security hardening
- PowerShell automation
- registry-based remediation
- compliance auditing
- operational security processes
- vulnerability management lifecycle operations

The remediation process demonstrated the ability to identify compliance findings, validate failure conditions, implement corrective actions manually and programmatically, and confirm successful remediation through rescanning and compliance verification.
