
# Path Traversal / Directory Traversal

## What is Path Traversal?

Path Traversal (also known as Directory Traversal) is a web security vulnerability that allows an attacker to access files and directories outside the intended application directory.

This vulnerability occurs when an application does not properly validate user-supplied file paths.

## Example

Suppose a website loads images using a URL like:

```text
/image?filename=profile.jpg
