# Web Application Security Risks

Web applications can contain different types of security weaknesses. Some common categories covered in this room are based on the OWASP Top Ten.

## Identification and Authentication Failures

Identification is the process of uniquely identifying a user, while authentication verifies that the user is who they claim to be.

Common weaknesses include:

- Unlimited login attempts, allowing brute-force attacks
- Weak or easily guessed passwords
- Storing passwords in plaintext

### Example

If a login page allows an attacker to repeatedly try passwords without rate limiting or account lockout, it can be vulnerable to brute-force attacks.

---

## Broken Access Control

Access control ensures that users can only access resources appropriate for their role.

Examples of weaknesses include:

- Giving users more privileges than they need
- Accessing another user's account or information
- Accessing authenticated pages without logging in

The **principle of least privilege** helps reduce these risks by giving users only the permissions necessary for their role.

---

## Injection

An injection vulnerability occurs when an application allows malicious input to be interpreted as code or commands.

A common cause is insufficient input validation or sanitisation.

Attackers may attempt to manipulate application input to make the system perform actions that were not intended by the developer.

---

## Cryptographic Failures

Cryptographic failures occur when sensitive information is not adequately protected.

Examples include:

- Sending sensitive information over HTTP instead of HTTPS
- Using weak cryptographic algorithms
- Using weak or default encryption keys
- Storing sensitive information without appropriate encryption

### HTTP vs HTTPS

**HTTP** does not provide encryption for data transmitted between the browser and server.

**HTTPS** uses encryption to protect data during transmission.

Sensitive information such as usernames, passwords, and payment details should be appropriately protected during transmission.

---

## Questions

### Q1. You discovered that the login page allows an unlimited number of login attempts without trying to slow down the user or lock the account. What is the category of this security risk?

**Answer:** `Identification and Authentication Failure`

Unlimited login attempts can allow attackers to perform brute-force attacks against user accounts.

### Q2. You noticed that the username and password are sent in cleartext without encryption. What is the category of this security risk?

**Answer:** `Cryptographic Failures`

Sending sensitive credentials in cleartext means the data is not adequately protected during transmission.

---

## Quick Reference

| Risk | Main concern |
|---|---|
| **Identification and Authentication Failures** | Weaknesses in identifying and authenticating users |
| **Broken Access Control** | Users accessing resources they should not access |
| **Injection** | Malicious input being interpreted as code or commands |
| **Cryptographic Failures** | Sensitive data not being adequately protected |

## Key Takeaway

Web application security requires protecting authentication, controlling access, validating user input, and properly protecting sensitive information.
