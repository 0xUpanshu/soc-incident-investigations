# NIST CSF – DoS Incident Report

## Overview

This portfolio activity analyzes a simulated Denial-of-Service (DoS) attack
against a multimedia company's internal network using the NIST Cybersecurity
Framework (CSF).

## Scenario

A multimedia company that provides web design, graphic design, and social
media marketing services to small businesses experienced a Denial-of-Service
(DoS) attack.

A malicious actor flooded the company's network with ICMP packets through an
unconfigured firewall. The attack overwhelmed network resources and caused
network services to stop responding. Normal internal network traffic could
not access network resources for approximately two hours.

The incident management team responded by blocking incoming ICMP packets,
taking non-critical network services offline, and restoring critical network
services.

Following the incident, the security team identified the unconfigured
firewall as the vulnerability that allowed the attack and implemented
additional firewall controls, source IP verification, network monitoring,
and IDS/IPS capabilities.

## Security Improvements

Following the incident, the organization implemented:

- ICMP rate limiting
- Source IP address verification
- Network traffic monitoring
- IDS/IPS controls

## Framework

The incident was analyzed using the five core functions of the NIST
Cybersecurity Framework:

**Identify → Protect → Detect → Respond → Recover**

The detailed incident analysis is provided in the report below.

## Report

[View Incident Report](./Incident_Report_Analysis.pdf)

## Skills Demonstrated

- Network security analysis
- DoS and ICMP flood analysis
- Firewall security
- Network monitoring
- IDS/IPS
- Incident response and recovery
- NIST Cybersecurity Framework (CSF)

## Source

This activity is based on the practice assignment from the **Google Cybersecurity Professional Certificate**.

The scenario and activity requirements are course-provided. The security analysis and recommendations are documented in the completed assessment included in this repository.