# Download Nessus Scan via Metasploit

Why would you want to do this? Well, because on my AWS pentesting boxes or during a penetration test I don't want to have to reverse tunnel, download, and then SCP the scan. This makes life significantly easier and I can perform an EyeWitness scan without ever leaving my terminal.

### Usage

Load the Nessus plugin

```bash
load Nessus
```

Authenticate to the Nessus instance

```bash
nessus_connect $username:$password@127.0.0.1:8834
```

List the scans avaialble in Nessus (pay attention to the ID of the scan you want to download)

```bash
nesssus_scan_list
```

Export the Nessus scan

```bash
Nessus_scan_export [ID] nessus
```

Download the Nessus scan to .msf

```bash
nessus_report_download [ID] [FILEID]
```

Report is accessible via /home/$USER/.msf4/local directory.

Rename the file to `$client.nessus`
