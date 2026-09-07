```text
            CBC MODE

 Plaintext
     |
     v
+---------+
| Block 1 |
+---------+
     |
     v
+---------+
| Block 2 |
+---------+
     |
     v
+---------+
| Block 3 |
+---------+

Padding Validation
       |
       v
Timing Variations
       |
       v
LUCKY13 Exposure
```


```console
$ openssl ciphers -v

ECDHE-RSA-AES128-GCM-SHA256
ECDHE-RSA-AES256-GCM-SHA384
ECDHE-RSA-CHACHA20-POLY1305

CBC suites not detected
```

```bash
$ ./tls-audit.sh

[+] TLS 1.3 enabled
[+] TLS 1.2 enabled
[+] Forward secrecy enabled
[+] AEAD only
[+] Compression disabled

Risk Score: LOW
```
