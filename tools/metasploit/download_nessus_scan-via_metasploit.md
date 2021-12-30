# Download Nessus Scan via Metasploit

Why would you want to do this? Well, because on my AWS pentesting boxes or during a penetration test I don't want to have to reverse tunnel, download, and then SCP the scan. This makes life significantly easier and I can perform an EyeWitness scan without ever leaving my terminal.

## Usage

1. Load the Nessus plugin

`load Nessus`

1. Authenticate to the Nessus instance

`nessus_connect [USERNAME]:[PASSWORD]@127.0.0.1:8834`

1. List the scans avaialble in Nessus (pay attention to the ID of the scan you want to download)

`nesssus_scan_list`

1. Export the Nessus scan

`Nessus_scan_export [ID] nessus`

1. Download the Nessus scan to .msf

`nessus_report_download [ID] [FILEID]`

1. Report is accessible via /home/$USER/.msf4/local directory.
2. Rename the file (\[ID-\[FILEID] to \[CLIENT].nessus
