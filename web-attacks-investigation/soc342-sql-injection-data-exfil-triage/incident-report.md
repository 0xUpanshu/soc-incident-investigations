# Incident Report – CVE-2025-53770 Exploitation

## 1. Alert Information

- Rule Name: SOC342 – CVE-2025-53770 SharePoint ToolShell Auth Bypass & RCE
- Severity: Critical
- Hostname: SharePoint01
- Source IP: 107.191.58.76
- Destination IP: 172.16.20.17
- HTTP Method: POST
- Target Endpoint: /layouts/15/ToolPane.aspx
- Device Action: Allowed

The alert indicated a suspicious unauthenticated POST request with a large payload targeting a vulnerable SharePoint endpoint.

---

## 2. Initial Analysis

The request matched known indicators of CVE-2025-53770 exploitation, which allows:

- Authentication bypass
- Remote Code Execution (RCE)

The payload size (7699 bytes) and spoofed referer further increased suspicion.

Since the device action was marked as "Allowed", the malicious request was successfully delivered to the server.

---

## 3. Endpoint Investigation

Further analysis was conducted on SharePoint01.

A suspicious PowerShell command was observed:

C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe -nop -w hidden -e <Base64_String>

Indicators of malicious intent:

- `-nop` to avoid profile loading
- `-w hidden` to execute without user visibility
- `-e` indicating encoded command execution

The Base64 string was decoded using CyberChef (UTF-16LE decoding).

The decoded output revealed malicious script execution consistent with post-exploitation behavior.

---

## 4. Attack Chain Identified

1. External attacker sent crafted POST request targeting SharePoint vulnerability.
2. Request was allowed and reached the internal server.
3. Exploit triggered PowerShell execution.
4. Encoded payload executed on the server.

This confirms exploitation progressed beyond initial attempt.

---

## 5. MITRE ATT&CK Mapping

- T1190 – Exploit Public-Facing Application
- T1059.001 – PowerShell
- T1027 – Obfuscated/Encoded Files or Information

---

## 6. Impact Assessment

The presence of encoded PowerShell execution strongly indicates successful remote code execution.

System integrity is considered compromised until proven otherwise.

---

## 7. Recommended Actions

- Immediately isolate SharePoint01 from network
- Block source IP 107.191.58.76
- Patch SharePoint against CVE-2025-53770
- Perform full forensic analysis
- Reset credentials associated with the server
- Review logs for additional persistence mechanisms

---

## 8. Final Verdict

**True Positive – Confirmed Exploitation with Malicious Execution Observed**