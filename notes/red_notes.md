---
description: >-
  Notes from various penetration testing engagements and CTFs that I thought
  would be worth documenting.
---

# Offensive Security Notes

1\. Search for whitelisted applications when looking to migrate and dump credentials. During a penetration test I was struggling to dump credentials with Kiwi as a PoC. Migrating into an AppSense application that is required to be whitelisted by endpoints can result in easy l00t. [This link](https://knowledge.broadcom.com/external/article/171640/dlp-endpoint-agent-causes-delays-when-fi.html) lists a few of the executables that I was able to migrate into with Meterpreter and proceed to execute Kiwi from, namely EMUser.exe.

2\. Time to Live

```bash
TTL > 64 it is most likely a Linux box
TTL > 128 it is most likely a Windows
TTL < 128 most likely some type of networking device.
```

3\. Some quick notes on organizing tooling:

* Download and place the tool into /opt/ (e.g., Aquatone).&#x20;
* Execute the following command on the Aquatone binary: `ln -s /opt/aquatone/aquatone /usr/local/bin/aquatone`

3\. Reverse shell preferences:

* External: Bind shell
* Internal: Reverse shell

4\. [Microsoft has a great reference](https://docs.microsoft.com/en-us/dotnet/framework/migration-guide/versions-and-dependencies) for .NET Framework & Windows OS Versions. We can then [use a precompiled binary from SharpCollection](https://github.com/Flangvik/SharpCollection) to exploit the system.

* Compile the binaries yourself.. Unless it's a CTF.

5\. Performing password spraying with [SprayCharles](https://github.com/Tw1sm/spraycharles) from my experience is more successful than using the [SprayingToolkit](https://github.com/byt3bl33d3r/SprayingToolkit). Ran into a situation on an engagement where multiple valid logins were reported as invalid by SprayingToolkit.&#x20;

6\. Kali Linux allows for multiple IP addresses to be set manually on an interface, allowing for you to set multiple callbacks in case one of your IP addresses gets banned. The following demonstrates a screenshot of this:

![](https://i.imgur.com/FYiHJX6.png)

7\. Download a Nessus scan via Metasploit:

```bash
# Load the Nessus plugin
load Nessus

# Authenticate to Nessus
nessus_connect $username:$password@127.0.0.1:8834

# List Available Nessus Scans (Pay attention to the ID)
nesssus_scan_list

# Export the Nessus Scan
Nessus_scan_export $id nessus

Download the Nessus scan to ~/.msf
nessus_report_download $id $fileid

# Report is then accessible in the ~/.msf4/local directory
# Rename the file to $client.nessus
```
