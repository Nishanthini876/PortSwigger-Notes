# Introduction to Server-Side Vulnerabilities

Server-side vulnerabilities are security weaknesses that exist in a web application's backend. Attackers can exploit these vulnerabilities to access sensitive information, bypass security controls, or perform unauthorized actions on the server.

Understanding server-side vulnerabilities is important for web security testing, penetration testing, and bug bounty hunting. Security researchers and bug bounty hunters often look for these vulnerabilities to help organizations identify and fix security issues before they can be exploited by malicious attackers.

---

# Path Traversal / Directory Traversal

## What is Path Traversal?

Path Traversal (also known as Directory Traversal) is a web security vulnerability that allows an attacker to access files and directories outside the intended application directory.

This vulnerability occurs when an application does not properly validate user-supplied file paths.

## Example

Suppose a website loads images using a URL like:

```text
/image?filename=profile.jpg
