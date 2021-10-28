# Domain Enumeration

## Enumerate AD CS

Dump and display certification authority information with Certutil.exe. This utility can be used to quickly identify if there is a certificate authority on the domain for AD CS attacks: \

```certutil.exe```

If we get a hit then we can browse to the host identifed with the following URL: \

```http://localhost/certsrv/```
