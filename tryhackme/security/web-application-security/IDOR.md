# Insecure Direct Object References (IDOR)

## What is IDOR?

**Insecure Direct Object Reference (IDOR)** is a type of **Broken Access Control** vulnerability.

It occurs when a web application uses user-controlled input, such as an ID or filename, to access an object without properly checking whether the user is authorised to access it.

## Example

A web application might use a URL such as:

```text
/products/product?id=52
/products/product?id=51
/products/product?id=53
/customers/user?id=16
Changing the ID to another user's ID could potentially expose that user's information if proper access controls are not implemented.

Why IDOR Happens
IDOR vulnerabilities commonly occur when an application:

Trusts user-supplied object identifiers

Uses predictable or sequential identifiers

Fails to verify whether the current user is authorised to access the requested object

Simply knowing the correct URL or object ID should not be enough to access another user's information.

Practical Example
In the TryHackMe exercise, an Inventory Management System was vulnerable to IDOR.

The task involved:

Reviewing user activity.

Identifying the user account responsible for malicious changes.

Reverting those changes.

Receiving a flag after successfully restoring the system.

Question
Q1. Check the other users to discover which user account was used to make the malicious changes and revert them. After reverting the changes, what is the flag that you have received?
Answer: THM{IDOR_EXPLORED}

Key Takeaway
IDOR occurs when an application allows users to access objects they are not authorised to access by manipulating a reference such as an ID or filename.

IDOR is a form of Broken Access Control.
