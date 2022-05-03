---
description: MITRE ATT&CK Reconnaissance, Sub-technique T1590.002
---

# Gather DNS Information

### Description

Subdomain enumeration is the process of finding valid resolvable subdomains for a companies domain(s). The more you can find, the more you can hack.&#x20;

### Google Dork

```bash
site:*.$domain -www)
```

### Sublist3r

Passively enumeration subdomains of a specified domain:

```bash
sublist3r.py -d $domain
```

Enumerate subdomains and utilize the 'brute force' module:

```bash
sublist3r.py -b -d $domain
```

{% embed url="https://github.com/aboul3la/Sublist3r" %}

### DNSRecon

Enumerate subdomains:

```bash
dnsrecon -d $domain
```

Enumerate subdomains and perform a zone transfer

```bash
dnsrecon -a -d $domain
```

{% embed url="https://github.com/darkoperator/dnsrecon" %}

### Amass

Retrieve the target domains ASN number:

```bash
amass enum -d $domain
```

{% embed url="https://github.com/OWASP/Amass" %}

### Gobuster

```bash
gobuster dns --domain $domain --wordlist $wordlist
```



{% embed url="https://github.com/OJ/gobuster" %}

### Additional Resources

{% embed url="https://securitytrails.com" %}

{% embed url="https://crt.sh" %}

{% embed url="https://dnsdumpster.com" %}
