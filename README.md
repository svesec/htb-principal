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

The exposed web application presented a login interface identified as **Principal Internal Platform**. Initial interaction with the application revealed a modern JavaScript-based front-end communicating with multiple backend API endpoints.

Analysis of the login functionality and client-side resources indicated that authentication was handled through token-based mechanisms. Further inspection of the application's JavaScript code exposed several internal API endpoints, including:

* `/api/dashboard`
* `/api/users`
* `/api/settings`
* `/api/auth/jwks`
* `/api/auth/login`

The presence of a publicly accessible JWKS endpoint and references to token validation logic suggested that the application's authentication model relied on JWT/JWE technology. This significantly narrowed the assessment focus toward authentication and authorization mechanisms.

The following evidence illustrates the identified attack surface and the client-side disclosure of authentication-related functionality.

![Login Page](evidence/screenshots/02_login_page.png)

![Login Request](evidence/screenshots/03_login_request_burp.png)

![Unauthorized API Access](evidence/screenshots/04_api_docs_unauthorized.png)

![JavaScript Token Logic](evidence/screenshots/05_js_token_logic.png)


## JWT/JWE Assessment

## Initial Access

## Privilege Escalation

## Findings

## Security Recommendations

## Conclusion
