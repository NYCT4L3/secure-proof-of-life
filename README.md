# Secure Proof-of-Life + Digital Legacy System

> 🚧 **Status: in development.** This README describes the design and roadmap.

A security-focused application that confirms a user is still active through regular check-ins. If they stop responding, it moves through reminders, a grace period and trusted-contact warnings, then triggers a **Dead Man's Switch** that releases encrypted information to chosen recipients.

## How it works

```
Check-ins → Missed check-in → Reminder → Grace period → Trusted-contact alert
        → Dead Man's Switch → Controlled release of vault items
```

The user can always cancel a pending trigger with the **"I'm OK"** override, and every cancellation is logged.

## Core components

- **Proof of Life:** configurable check-in intervals, reminders, history, current status
- **Dead Man's Switch:** configurable inactivity period, grace period, recipients and actions
- **Digital Legacy Vault:** encrypted messages, documents and instructions, each with its own recipient, release condition and delay
- **Lost Device Mode:** lock down the account, revoke sessions and tokens, register a replacement device
- **Emergency Mode:** user-activated alert to trusted contacts, separate from Proof of Life
- **Trusted contacts and devices:** invitations, permissions, per-item access
- **Audit log and notifications:** push, email, SMS and in-app

## Security design

- MFA and step-up authentication for high-risk actions
- Encryption at rest, TLS in transit, hashed passwords, secure key management
- Anti-spoofing and false-trigger protection: signed requests, nonces and timestamps, replay protection, rate limiting
- Compromise detection: new devices, unusual logins, failed attempts, MFA changes
- Recovery mechanisms designed **not to become a backdoor**
- Administrators cannot read vault contents (least privilege)

## Planned scope

**MVP:** registration and MFA, check-ins, missed-check-in detection, grace period, Dead Man's Switch, trusted contacts, encrypted vault with controlled release, Lost Device Mode, device and session management, notifications, audit logs, basic anti-spoofing

**Next:** multiple notification channels, location opt-in, step-up auth, suspicious-login detection, account recovery, admin dashboard

**Future:** biometric proof of life, anomaly detection, hardware security keys, zero-knowledge architecture, mobile app

## Security testing (planned)

Each test will be documented as **attack → vulnerability → mitigation → secure result**:
brute force, credential stuffing, session hijacking, replay attacks, token theft, IDOR, privilege escalation, SQL injection, XSS, CSRF, API abuse, notification spoofing and check-in spoofing.

## Ethics

All security testing is performed only against my own deployment in an isolated lab, using test data.
