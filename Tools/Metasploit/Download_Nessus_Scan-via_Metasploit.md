# Download Nessus Scan via Metasploit

**Description:** Why would you want to do this? Well, because on my AWS pentesting boxes or during a penetration test I don't want to have to reverse tunnel, download, and then SCP the scan. This makes life significantly easier and I can perform an EyeWitness scan without ever leaving my terminal. 

## Usage

1. Load the Nessus plugin 

```load Nessus```

2. Authenticate to the Nessus instance

```nessus_connect [USERNAME]:[PASSWORD]@127.0.0.1:8834```

3. List the scans avaialble in Nessus (pay attention to the ID of the scan you want to download)

```nesssus_scan_list```

4. Export the Nessus scan

```Nessus_scan_export [ID] nessus```

5. Download the Nessus scan to .msf

```nessus_report_download [ID] [FILEID]```

6. Report is accessible via /home/$USER/.msf4/local directory. 

7. Rename the file ([ID-[FILEID] to [CLIENT].nessus
