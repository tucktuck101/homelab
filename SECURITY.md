# Security Policy

Security is a core requirement of this project.

## Reporting a Vulnerability

Do not report security vulnerabilities, exposed credentials, sensitive infrastructure information, or suspected secret leakage through a public GitHub Issue.

Please use GitHub's **Private vulnerability reporting** feature for this repository.

If private vulnerability reporting is unavailable, contact:

`hello@clankerops.nz`

## Sensitive Information

This repository must not contain:

* passwords
* API keys or tokens
* private keys
* production credentials
* recovery material
* unencrypted secrets
* other information that could provide unauthorized access to infrastructure or services

Configuration examples should use placeholders or non-sensitive example values.

## Accidental Disclosure

If sensitive information is discovered in the repository or its Git history, treat the affected credential or secret as compromised and rotate or revoke it before addressing the repository history.
