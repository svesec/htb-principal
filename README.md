# Principal - Security Assessment Report

Security assessment of the Hack The Box machine Principal, focusing on JWT/JWE abuse, SSH certificate authentication, and privilege escalation.

## Overview

This report documents a security assessment of the Hack The Box machine Principal. The objective of the assessment was to identify and validate security weaknesses across the exposed services and application components, determine their potential impact, and demonstrate the resulting attack path.

The assessment identified weaknesses in the application's authentication and authorization design, allowing administrative access through a crafted token. Further analysis revealed information disclosure related to SSH certificate-based authentication, which ultimately enabled privilege escalation and full compromise of the target system.

The attack chain progressed from initial reconnaissance and web application analysis to administrative API access, authenticated system access, and root-level compromise.

## Scope

| Item             | Details                                                                            |
| ---------------- | ---------------------------------------------------------------------------------- |
| Target           | Principal                                                                          |
| Platform         | Hack The Box                                                                       |
| Operating System | Linux                                                                              |
| Assessment Type  | Black Box Security Assessment                                                      |
| Objective        | Identify and validate security weaknesses leading to system compromise             |
| Out of Scope     | Denial of Service (DoS), brute-force attacks, and attacks against external systems |

## Methodology

The assessment followed a structured security testing methodology designed to identify, validate, and assess security weaknesses in a controlled environment.

The testing process consisted of the following phases:

1. Reconnaissance and service enumeration
2. Attack surface analysis
3. Authentication and authorization assessment
4. Controlled exploitation
5. Privilege escalation analysis
6. Risk assessment and security recommendations

Each finding was validated through controlled testing and supported by technical evidence collected during the assessment.

## Reconnaissance

Initial reconnaissance identified two exposed services on the target system.

| Port | Service | Version       |
| ---- | ------- | ------------- |
| 22   | SSH     | OpenSSH 9.6p1 |
| 8080 | HTTP    | Jetty         |

The HTTP service on port 8080 redirected users to a login interface identified as Principal Internal Platform. Additionally, HTTP response headers revealed the use of the pac4j-jwt framework, providing an early indication that authentication functionality was likely based on JWT technology.

These findings established the initial attack surface and guided further analysis toward the web application and its authentication mechanisms.

![Nmap Scan](evidence/screenshots/01_nmap_ports.png)

## Attack Surface Analysis

## JWT/JWE Assessment

## Initial Access

## Privilege Escalation

## Findings

## Security Recommendations

## Conclusion
