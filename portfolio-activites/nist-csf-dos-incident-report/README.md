# NIST CSF – DoS Incident Report

## Overview

This portfolio activity analyzes a simulated Denial-of-Service (DoS) attack
against a multimedia company's internal network using the NIST Cybersecurity
Framework (CSF).

## Incident

A malicious actor flooded the organization's network with ICMP packets
through an unconfigured firewall. The attack overwhelmed network resources
and prevented normal internal traffic from accessing network services for
approximately two hours.

The incident was contained by blocking incoming ICMP traffic, taking
non-critical services offline, and restoring critical services.

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