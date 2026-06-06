# Server-Side Request Forgery (SSRF)

## Overview

**Server-Side Request Forgery (SSRF)** is a web security vulnerability that allows an attacker to make the server send requests to unintended destinations.

In an SSRF attack, the attacker tricks the vulnerable server into sending requests to internal or external systems that are normally inaccessible.

---

## Types of SSRF

### 1. Basic SSRF Against the Local Server

In this type of attack, the vulnerable application sends requests to services running on the same server.

#### Impact
- Access to internal resources.
- Access to localhost services.
- Exposure of administrative interfaces.

#### Examples
- Accessing `localhost` services.
- Reaching hidden admin panels.
- Accessing internal APIs.

---

### 2. SSRF Against Another Back-End System

In this scenario, the vulnerable server sends requests to other systems within the organization's internal network.

#### Impact
- Access to internal applications.
- Exposure of sensitive information.
- Access to administrative interfaces.
- Interaction with private network services.

---

## Identifying SSRF Vulnerabilities

### Signs of SSRF

Look for functionality that fetches remote resources using user-supplied input, such as:

- URL parameters
- Image fetchers
- Webhooks
- PDF generators
- File import features

### Testing Process

1. Identify input fields that accept URLs.
2. Observe how the application processes the request.
3. Modify the URL parameter.
4. Analyze the server response.
5. Look for evidence of internal resource access.

---

## SSRF Testing Using Burp Suite

### Workflow

```text
Intercept Request
        ↓
Send to Repeater
        ↓
Modify URL Parameter
        ↓
Forward Request
        ↓
Analyze Response
        ↓
Confirm SSRF
```

### Steps

1. Capture the request using Burp Suite.
2. Send the request to Repeater.
3. Modify the target URL parameter.
4. Forward the request.
5. Observe the response.
6. Check the HTTP status code.
7. Determine whether internal resources were accessed.

---

## Indicators of Successful SSRF

A successful SSRF attack may result in:

- Different response content.
- Unexpected HTTP status codes.
- Access to internal resources.
- Access to localhost services.
- Access to private IP ranges.
- Retrieval of hidden or sensitive information.

---

## Common Targets

- Internal web applications
- Administrative panels
- Cloud metadata services
- Internal APIs
- Database management interfaces
- Monitoring systems

---

## Mitigation Strategies

### Input Validation
- Validate all user-supplied URLs.
- Restrict allowed URL formats.

### Allowlisting
- Permit requests only to trusted domains.
- Block requests to internal IP ranges.

### Network Segmentation
- Isolate sensitive internal services.
- Limit communication between network segments.

### Access Controls
- Restrict access to administrative interfaces.
- Enforce least-privilege principles.

---

## Key Points

- SSRF stands for **Server-Side Request Forgery**.
- It allows attackers to make the server send unintended requests.
- Internal systems are often the primary target.
- Burp Suite is commonly used to identify and test SSRF vulnerabilities.
- URL parameters are frequently involved in SSRF attacks.
- Proper validation and network restrictions help prevent SSRF.

---

## Quick Revision

| Topic | Summary |
|---------|---------|
| SSRF | Server-Side Request Forgery |
| Goal | Force the server to send unintended requests |
| Targets | Localhost, internal services, back-end systems |
| Testing Tool | Burp Suite |
| Common Method | Manipulating URL parameters |
| Indicators | Response changes, status codes, internal data access |
| Prevention | Input validation, allowlists, network segmentation |

---

## Exam Definition

**Server-Side Request Forgery (SSRF)** is a web security vulnerability that enables an attacker to induce a server-side application to make requests to unintended locations, potentially exposing internal systems, sensitive data, or administrative interfaces.
