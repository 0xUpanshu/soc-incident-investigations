# Incident Report – CVE-2024-24919 Exploitation on Check Point Security Gateway

## 1. Alert Details

Rule Name: SOC287 – Arbitrary File Read on Check Point Security Gateway  
CVE: CVE-2024-24919  
Severity: High  
Hostname: CP-Spark-Gateway-01  
Destination IP: 172.16.20.146  
Source IP: 203.160.68.12  
HTTP Method: POST  
Target Endpoint: /clients/MyCRL  
Device Action: Allowed  

The alert indicates a potential exploitation attempt targeting a vulnerable component of the Check Point Security Gateway.

---

## 2. Initial Analysis

The HTTP request contains the following payload:

aCSHELL/../../../../../../../../etc/passwd

The sequence `../` is used for directory traversal, allowing an attacker to move outside the intended application directory and access sensitive files on the system.

The attacker attempted to retrieve the `/etc/passwd` file, which is commonly targeted in path traversal attacks to confirm file disclosure.

The request originated from an external public IP address and targeted the internal security gateway.

---

## 3. Vulnerability Context

CVE-2024-24919 is a known vulnerability affecting Check Point Security Gateways that allows attackers to read arbitrary files through specially crafted requests.

Successful exploitation can expose sensitive system files and configuration data, which may aid attackers in further compromise.

---

## 4. Attack Behavior

The attack followed a typical path traversal exploitation pattern:

1. The attacker sent a crafted POST request to the vulnerable endpoint `/clients/MyCRL`.
2. The payload used directory traversal sequences to escape the application directory.
3. The attacker attempted to access the sensitive system file `/etc/passwd`.
4. The request reached the gateway as the device action was marked as **Allowed**.

The payload structure and detection rule strongly indicate exploitation of CVE-2024-24919.

---

## 5. MITRE ATT&CK Mapping

T1190 – Exploit Public-Facing Application  
T1006 – Path Traversal  

---

## 6. Impact Assessment

The exploitation allowed unauthorized access to sensitive system files on the gateway.

Exposure of system files such as `/etc/passwd` may reveal information about system users and environment configuration, which could assist attackers in further attacks.

Due to the potential impact, the incident was escalated according to the SOC playbook.

---

## 7. Response and Escalation

According to the SOC response playbook, this incident requires **Tier-2 escalation** due to confirmed exploitation.

Recommended actions include:

- Escalate the incident to Tier-2 incident response team
- Patch the gateway against CVE-2024-24919
- Block the malicious source IP
- Review system logs for additional exploitation attempts
- Monitor for further suspicious activity

---

## 8. Final Verdict

**True Positive – Successful Exploitation**

The activity represents a confirmed path traversal attack exploiting CVE-2024-24919 on the Check Point Security Gateway.