# File Upload Vulnerabilities

## Overview

File Upload Vulnerabilities occur when a web application allows users to upload files without properly validating their type, content, or destination.

Attackers can exploit these weaknesses to upload malicious files and potentially gain control of the server.

---

## Common Risks

- Remote Code Execution (RCE)
- Web Shell Upload
- Malware Distribution
- Data Theft
- Server Compromise

---

## Lab Procedure

### Step 1: Intercept the Upload Request

- Upload a normal image file.
- Capture the request using Burp Suite.
- Send the request to Repeater.

### Step 2: Modify the Request

- Delete the original image content.
- Replace it with malicious file content.
- Change the file name extension to `.php`.
- Modify the Content-Type if required.

### Step 3: Upload the File

- Forward the modified request.
- Verify whether the application accepts the file.

### Step 4: Execute the Uploaded File

- Access the uploaded PHP file through the browser.
- If the server executes the file, the vulnerability is confirmed.

---

## Example Attack Flow

```text
Upload Image
      ↓
Intercept Request
      ↓
Send to Repeater
      ↓
Replace with PHP File
      ↓
Change File Name
      ↓
Forward Request
      ↓
Access Uploaded File
      ↓
Code Execution
```

---

## Prevention

- Validate file extensions.
- Validate MIME types.
- Store uploads outside the web root.
- Rename uploaded files.
- Scan uploaded files for malware.
- Restrict executable file uploads.

---

## Key Points

- File upload functionality can be dangerous if not secured.
- Attackers often attempt to upload executable files.
- Burp Suite can be used to manipulate upload requests.
- Proper validation is essential to prevent exploitation.

---

# OS Command Injection

## Overview

OS Command Injection is a vulnerability that allows attackers to execute operating system commands on the server.

This occurs when user input is incorporated into system commands without proper sanitization.

---

## Common Commands Used During Testing

### Linux Commands

```bash
whoami
hostname
pwd
ls
```

### Windows Commands

```cmd
whoami
hostname
ipconfig
dir
```

---

## Lab Procedure

### Step 1: Identify Input Points

Look for features such as:

- Stock Check
- Product Availability Check
- Ping Utilities
- Diagnostic Tools

### Step 2: Intercept the Request

- Capture the request using Burp Suite.
- Send it to Repeater.

### Step 3: Inject Commands

Append operating system commands to the parameter value.

### Step 4: Analyze the Response

Check whether command output appears in the server response.

---

## Typical Testing Workflow

```text
Find Vulnerable Parameter
          ↓
Intercept Request
          ↓
Send to Repeater
          ↓
Inject Command
          ↓
Forward Request
          ↓
Analyze Response
          ↓
Confirm Vulnerability
```

---

## Indicators of Successful Command Injection

- Command output appears in the response.
- Server information is disclosed.
- Unexpected behavior occurs.
- System details become visible.

---

## Impact

- Remote Code Execution
- Server Takeover
- Data Disclosure
- Privilege Escalation
- Internal Network Access

---

## Prevention

- Avoid system command execution when possible.
- Validate all user input.
- Use allowlists.
- Implement parameterized APIs.
- Run applications with minimal privileges.

---

## Key Points

- OS Command Injection allows execution of system commands.
- It occurs due to improper input handling.
- Burp Suite is commonly used for testing.
- Successful exploitation can lead to full server compromise.

---

## Quick Revision

| Vulnerability | Goal |
|--------------|------|
| File Upload Vulnerability | Upload and execute malicious files |
| OS Command Injection | Execute operating system commands |

| Tool | Usage |
|--------|--------|
| Burp Suite | Intercept and modify requests |
| Repeater | Test modified requests |
| Browser | Verify exploitation results |
