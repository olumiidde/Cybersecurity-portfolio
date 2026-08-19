# Security Risk Assessment Report

> Fictional scenario. Acting as a security analyst for a social media organization that recently experienced a major data breach exposing customer names and addresses, this assessment identifies network hardening methods to prevent future incidents.

## Background

Following the breach, an inspection of the organization's network uncovered four major vulnerabilities:

1. Employees share passwords with one another.
2. The admin password for the database is set to the default.
3. Firewalls have no rules in place to filter inbound/outbound traffic.
4. Multi-factor authentication (MFA) is not in use.

Left unaddressed, these vulnerabilities leave the organization at risk of another data breach or further attacks. This report analyzes the incident and recommends hardening methods to secure the network going forward.

## Part 1: Recommended Hardening Tools and Methods

Three hardening tools/methods are recommended to address the vulnerabilities found:

1. **Implement multi-factor authentication (MFA)** — MFA requires users to verify their identity using more than one method before accessing an application. Common MFA methods include fingerprint scans, ID cards, PIN numbers, and passwords.

2. **Set and enforce strong password policies** — Policies can define rules around password length, acceptable characters, and discourage password sharing. They can also include lockout rules, such as revoking access after five unsuccessful login attempts.

3. **Perform regular firewall maintenance** — Security configurations should be checked and updated regularly to stay ahead of emerging threats.

## Part 2: Recommendation Rationale

**MFA:** Enforcing MFA adds a layer of security beyond a password alone. It reduces the likelihood that a malicious actor can access the network via a brute force or related attack, since additional effort is required to authenticate through more than one method. MFA also discourages password sharing — since the recipient of a shared password would still need to possess the additional authentication factor, sharing a password alone becomes far less useful to a would-be attacker.

**Password policy:** Creating and enforcing a password policy makes it significantly harder for malicious actors to access the network. Measures such as suspending an account after a set number of failed login attempts can prevent successful brute force attacks. Increasing password complexity, requiring more frequent password updates, and disallowing password reuse further slow down attempts to infiltrate the network.

**Firewall maintenance:** Firewall maintenance should be an ongoing process. Network administrators should ensure firewall rules reflect current standards for allowed and denied traffic, and that traffic from suspicious sources is added to a denied list. Rules should be updated whenever a security event occurs — particularly one that allowed suspicious traffic into the network. This measure also helps protect against DoS and DDoS attacks.
