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
