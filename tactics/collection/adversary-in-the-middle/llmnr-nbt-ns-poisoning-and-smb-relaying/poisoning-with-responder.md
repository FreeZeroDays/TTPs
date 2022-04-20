---
description: Guide on using Responder.py to attack a network and obtain Net-NTLM hashes.
---

# Poisoning with Responder

### Description

Responder is the go-to tool for poisoning LLMNR, NBT-NS, and mDNS requests. NBT-NS, LLMNR and mDNS can broadcast queries to the entire network, but no measures are taken to verify the responses. As an attacker, we can exploit this by listening to the queries, spoofing the response, and then obtaining to the account being used to authenticate.&#x20;

{% embed url="https://github.com/lgandx/Responder" %}

### Usage

I always recommend running Responder in Analyze mode to begin your assessment. This will help identify DNS replacement protocols such as LLMNR and NBT-NS. Additionally, we can still capture hashes in Analyze mode, an example of this would be when a client has a 'network spider' for patch management.&#x20;

Run Responder in Analyze mode first to observe traffic on the network:

```bash
responder -I eth0 -A
```

After identifying the protocols, we can rerun Responder with the parameters to poison:

```bash
responder -I eth0 -dwP
```

### Output In-scope Hosts from Responder

Recently on a penetration test I had a request from a client to be provided with only "In-Scope" hosts that were in the Responder-logs. This is because they wanted an actionable list of hosts to remediate for compliance rather than "your entire domain is rekt".&#x20;

If this is ever an ask, I found out a pretty easy way to grep out hosts from IPs within scope and provide this ask to a client:

Place the in-scope hosts into a file. For this example, it will be titled `InScopeHosts.txt`

```bash
> cat InScopeHosts.txt

127.0.0.1
127.0.0.2
127.0.0.3
```

Grep out the Responder-Session log to only IP Addresses:

```bash
cat Responder-logs | grep -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}’ ResponderIPs.txt
```

Compare the two files with grep. These commands will pipe duplicate IPs between the files into a new one (use your preferred)

```bash
egrep "cat InScopeHosts.txt|xargs -I {} echo -n '|{}'|sed -e 's/^|//'” ResponderIPs.txt > RepeatedIPs.txt
```

```bash
cat PreviouslyVulnerableIPs.txt`|xargs -I {} echo -n '|{}'|sed -e 's/^|//'" ResponderLogIPs.txt
```

Remove duplicates from the files using Excel (I find this easiest since I'll paste it into a report, but sort also works)

If the client has provided CIDRs then break these into smaller lists via your choice of tool. Personally, I like using nmap:

```bash
nmap -sL -n 127.0.0.0/24 | awk '/Nmap scan report/{print $NF}’
```

### References

{% embed url="https://www.cynet.com/attack-techniques-hands-on/llmnr-nbt-ns-poisoning-and-credential-access-using-responder" %}

{% embed url="https://www.trustedsec.com/blog/a-comprehensive-guide-on-relaying-anno-2022" %}
