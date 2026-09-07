# TLS Hardening Lab

A practical laboratory demonstrating TLS configuration analysis and hardening techniques.

The objective is to show how legacy cipher support can increase cryptographic attack surface and how modern TLS policies reduce exposure.

---

## Security Scenario

A representative perimeter service was assessed to review its TLS posture.

The environment already mitigated several historical TLS vulnerabilities:

* Heartbleed
* CCS Injection
* CRIME
* POODLE
* ROBOT
* RC4-related weaknesses

However, CBC-based cipher suites remained available.

While not immediately exploitable in most scenarios, CBC support increases exposure to timing-based attacks such as:

* LUCKY13 (CVE-2013-0169)

---

## Architecture

```text
                   Internet
                       |
                       v
              +----------------+
              | Load Balancer  |
              +----------------+
                       |
                       v
              +----------------+
              | Apache Server  |
              +----------------+
```

---

## Assessment Workflow

```text
+---------------------+
| TLS Enumeration     |
+----------+----------+
           |
           v
+---------------------+
| Cipher Analysis     |
+----------+----------+
           |
           v
+---------------------+
| Risk Evaluation     |
+----------+----------+
           |
           v
+---------------------+
| TLS Hardening       |
+----------+----------+
           |
           v
+---------------------+
| Validation Scan     |
+---------------------+
```

---

## Initial Findings

```console
$ tls-scan target.example

TLS 1.0       ENABLED
TLS 1.1       ENABLED
TLS 1.2       ENABLED

CBC CIPHERS   PRESENT
AEAD CIPHERS  PRESENT

RISK LEVEL    MEDIUM
```

---

## Hardening Goals

* Remove obsolete TLS versions
* Remove CBC cipher suites
* Prefer AEAD cipher suites
* Enforce Forward Secrecy
* Disable TLS compression
* Disable session tickets where appropriate

---

## Result

```console
$ tls-scan hardened.example

TLS 1.0       DISABLED
TLS 1.1       DISABLED
TLS 1.2       ENABLED
TLS 1.3       ENABLED

CBC CIPHERS   REMOVED
AEAD CIPHERS  ENABLED

RISK LEVEL    REDUCED
```

---

## Disclaimer

This repository is an educational reconstruction.

No customer names, domains, IP addresses, certificates, credentials, logs, or infrastructure identifiers are included.

