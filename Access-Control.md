# Access Control Vulnerabilities

## What is Access Control?

Access control is a security mechanism that determines what actions a user is allowed to perform within an application.

Different users have different levels of access. For example:

- Regular users have limited permissions.
- Administrators (Admins) have higher privileges and can manage users, settings, and sensitive data.

Access control vulnerabilities occur when an application fails to properly enforce these restrictions, allowing users to perform actions beyond their intended permissions.

---

## Impact

If an attacker gains unauthorized access to administrative functions, they may be able to:

- View sensitive company information
- Access user data
- Modify application settings
- Perform unauthorized administrative actions

---

## Vertical Privilege Escalation

Vertical privilege escalation occurs when a lower-privileged user gains access to higher-privileged functionality.

Example:

- User → Limited permissions
- Admin → Full permissions

If a normal user can access admin-only features, the application may be vulnerable to vertical privilege escalation.

---

## Common Causes

Access control vulnerabilities may occur because of:

- Missing authorization checks
- Misconfigured permissions
- Exposed administrative functionality
- Insecure application design

---

## Common Discovery Methods

Security testers often look for:

- Hidden administrative URLs
- Administrative panels
- Exposed functionality in client-side code
- References to privileged features within JavaScript files

Examples:

```text
/admin
/administrator
/admin-panel
```

---

## Prevention

- Enforce server-side authorization checks
- Apply the principle of least privilege
- Restrict access to administrative functions
- Regularly test access controls
- Validate permissions for every request

---

## Key Takeaway

Access control vulnerabilities occur when users can access functionality or data that should be restricted. Proper authorization checks are essential to ensure users can only perform actions permitted by their assigned role.


## Lab Walkthrough

### Initial Access

1. Check the application using the provided credentials:

   * Username: `admin`
   * Password: *(lab-provided)*

2. Log in to the account and inspect the available functionality.

---

### Analysis

* Observe the login and account-management requests using Burp Suite.
* Review account-related requests and responses.
* Identify any unusual behavior in account settings or account details functionality.
* Pay attention to parameters that control user account information.

---

### Testing

* Intercept the relevant request.
* Modify the request parameters.
* Forward the modified request to the application.
* Observe whether changes can be applied to another user's account.

---

### Key Observation

* Account-related actions may rely on client-controlled parameters.
* If authorization checks are missing, an attacker may be able to modify information belonging to another user.

---

### Tools Used

* Burp Suite Proxy
* Repeater
* Browser Developer Tools

---

### Lessons Learned

* Always inspect account-management requests.
* Test whether user identifiers can be manipulated.
* Verify that the server performs proper authorization checks before processing sensitive actions.


## Steps

1. Log in using the provided credentials.
2. Navigate to **My Account**.
3. Intercept the account-related request using Burp Suite.
4. Send the request to Repeater.
5. Identify user-controlled parameters.
6. Modify the parameter value to target another account.
7. Forward the modified request.
8. Observe that the application accepts the change.
9. Verify that the access-control vulnerability can be exploited.
10. Lab solved.

## Tools Used

- Burp Suite Proxy
- Repeater

## Key Learning

- Never trust client-supplied user identifiers.
- Sensitive account actions must be validated server-side.
- Missing authorization checks can lead to privilege escalation or unauthorized account modification.

## Status

✅ Lab Completed
  
# Horizontal Privilege Escalation

## Definition

Horizontal privilege escalation occurs when a user is able to access resources or perform actions that belong to another user with the same privilege level.

Instead of gaining administrator privileges, the attacker moves sideways between accounts.

---

## Common Causes

* Missing access-control checks
* Insecure Direct Object References (IDOR)
* Predictable user identifiers
* Client-side authorization controls

---

## IDOR (Insecure Direct Object Reference)

An IDOR vulnerability exists when an application exposes a direct reference to an object (such as a user ID, account number, or document ID) and fails to verify whether the user is authorized to access it.

### Example

```http
GET /my-account?id=123
```

An attacker changes:

```http
GET /my-account?id=124
```

If the application returns another user's data without verifying permissions, an IDOR vulnerability exists.

---

## Key Takeaways

* Access control must be enforced on the server side.
* User-controlled identifiers should never be trusted.
* Every request should verify that the authenticated user is authorized to access the requested resource.
* IDOR is one of the most common causes of horizontal privilege escalation.

