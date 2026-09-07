# After Hardening

## Protocol Enumeration

```console
$ openssl s_client -connect target:443

Protocol Support

TLS 1.0    DISABLED
TLS 1.1    DISABLED
TLS 1.2    ENABLED
TLS 1.3    ENABLED
```

## Cipher Enumeration

```console
$ testssl.sh target

Detected Cipher Categories

ECDHE + AES128-GCM
ECDHE + AES256-GCM
ECDHE + CHACHA20-POLY1305
```

## Security Observations

```text
[+] CBC Cipher Suites    REMOVED
[+] AEAD Cipher Suites   ENABLED
[+] Forward Secrecy      ENABLED
[+] TLS Compression      DISABLED
```

## Security Outcome

```text
Attack Surface Reduction

Before
------
CBC Present
Legacy Protocols Present

After
-----
CBC Removed
Modern AEAD Only
TLS 1.2+
```
