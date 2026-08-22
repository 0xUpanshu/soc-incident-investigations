# SOC287 – CVE-2024-24919 Check Point Security Gateway Arbitrary File Read

## Summary

A high severity alert was triggered indicating a possible exploitation attempt targeting the Check Point Security Gateway (CP-Spark-Gateway-01).

The alert was associated with CVE-2024-24919, a vulnerability that allows unauthorized file read through a path traversal technique.

Analysis of the HTTP request revealed a malicious payload attempting to access the sensitive system file `/etc/passwd` using directory traversal:

aCSHELL/../../../../../../../../etc/passwd

The request originated from an external public IP address (203.160.68.12) and targeted the internal gateway service (172.16.20.146).

The payload pattern matches known exploitation techniques associated with CVE-2024-24919. According to the SOC playbook, this activity requires **Tier-2 escalation** due to the potential exposure of sensitive system files.

Based on the investigation findings, the alert was classified as:

**True Positive – Successful Exploitation (Arbitrary File Read via Path Traversal)**

The incident was escalated to Tier-2 for further investigation and remediation.