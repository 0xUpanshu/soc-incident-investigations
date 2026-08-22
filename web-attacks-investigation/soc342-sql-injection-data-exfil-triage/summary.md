# SOC342 – CVE-2025-53770 SharePoint ToolShell Auth Bypass & RCE

## Summary

A critical security alert was triggered for a suspected exploitation attempt targeting an internal SharePoint server (SharePoint01).

The alert indicated a POST request sent to `/layouts/15/ToolPane.aspx` with a large payload size and spoofed referer, matching known exploitation patterns of CVE-2025-53770.

The request was marked as **Allowed**, meaning it successfully reached the server.

During endpoint investigation, suspicious PowerShell activity was observed. The command included:

- `-nop` (No profile)
- `-w hidden` (Hidden execution)
- `-e` (Base64 encoded command)

The encoded PowerShell payload was decoded and revealed malicious behavior consistent with post-exploitation activity.

Based on web logs and endpoint telemetry, this case was classified as:

**True Positive – Confirmed Exploitation with Malicious Execution**

Immediate containment and further forensic investigation were recommended.