# Domain Enumeration

## Enumerate AD CS

Dump and display certification authority information with Certutil.exe. This utility can be used to quickly identify if there is a certificate authority on the domain for AD CS attacks:

```
certutil.exe
```

If we get a hit then we can browse to the host identifed with the following URL: `http://localhost/certsrv/`\


## Enumerate Print Spooler Service

Enumerate Print Spooler service with ItWasAllADream:\
`docker run -it itwasalladream -u [USERNAME] -p [PASSWORD] -d [DOMAIN] [TARGET] -v`

Enumerate Print Spooler service with Impacket:\
`python rpcdump.py @[TARGET] | egrep 'MS-RPRN|MS-PAR'`

SpoolerScan is a great tool if you already have access to the machine:\
`.\SpoolerScan.ps1`
