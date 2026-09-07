# Before Hardening

## Protocol Enumeration

```console
$ openssl s_client -connect target:443

Protocol Support

TLS 1.0    AVAILABLE
TLS 1.1    AVAILABLE
TLS 1.2    AVAILABLE
```

## Cipher Enumeration

```console
$ testssl.sh target

Detected Cipher Categories

ECDHE + AES128-GCM
ECDHE + AES256-GCM
ECDHE + AES128-CBC
ECDHE + AES256-CBC
```

## Security Observations

```text
[+] Heartbleed           NOT DETECTED
[+] POODLE               NOT DETECTED
[+] ROBOT                NOT DETECTED
[+] RC4                  NOT DETECTED
[!] CBC Cipher Suites    PRESENT
```

## Risk Assessment

```text
Likelihood: Medium
Impact: Medium

Finding:
CBC-based TLS cipher suites remain enabled.

Associated Attack:
LUCKY13 (CVE-2013-0169)
```
