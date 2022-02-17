# Table of contents

* [TTPs](README.md)
* [Submission Template](template.md)

## Red Team

* [Reconnaissance](red-team/reconnaissance/README.md)
  * [Gather Employee Emails](red-team/reconnaissance/gather\_employee\_emails\_and\_usernames.md)
  * [Find IP Addresses Owned by a Company](red-team/reconnaissance/identify\_ip\_addresses\_owned\_by\_a\_company.md)
* [Initial Access](red-team/initial\_access/README.md)
  * [Phishing](red-team/initial\_access/phishing/README.md)
    * [Creating Templates](red-team/initial\_access/phishing/creating\_templates.md)
    * [Phishing Methodology](red-team/initial\_access/phishing/phishing\_methodology.md)
    * [Picking a Time to Send Phishing Emails](red-team/initial\_access/phishing/picking\_a\_time.md)
* [Execution](red-team/exploitation/README.md)
  * [Exploitation with PowerShell](red-team/exploitation/exploitation\_with\_powershell.md)
  * [Easy Hacks](red-team/exploitation/easy\_hacks.md)
* [Persistence](red-team/persistence/README.md)
  * [Create Golden Ticket](red-team/persistence/create\_golden\_ticket.md)
  * [Skeleton Key](red-team/persistence/skeleton\_key.md)
* [Privilege Escalation](red-team/privilege\_escalation/README.md)
  * [Linux](red-team/privilege\_escalation/linux.md)
  * [Windows](red-team/privilege\_escalation/windows/README.md)
    * [Privilege Escalation with SeLoadDriverPrivilege](red-team/privilege\_escalation/windows/seloaddriverprivilege.md)
    * [Juicy Potato](red-team/privilege\_escalation/windows/juicy-potato.md)
* [Defense Evasion](red-team/defense\_evasion/README.md)
  * [Disable Antivirus](red-team/defense\_evasion/disable\_antivirus.md)
* [Discovery](red-team/discovery/README.md)
  * [Domain Enumeration](red-team/discovery/domain\_enumeration.md)
  * [Recon while Pivoting](red-team/discovery/recon\_while\_pivoting.md)
  * [BloodHound Queries](red-team/discovery/bloodhound\_queries.md)
* [Credential Access](red-team/credential\_access/README.md)
  * [Unsecured Credentials](red-team/credential\_access/unsecured\_credentials-1/README.md)
    * [Finding Credentials with MANSPIDER](red-team/credential\_access/unsecured\_credentials-1/finding\_credentials\_with\_manspider.md)
  * [Brute Force](red-team/credential\_access/brute\_force/README.md)
    * [Password Cracking](red-team/credential\_access/brute\_force/password\_cracking/README.md)
      * [Hashcat Tips](red-team/credential\_access/brute\_force/password\_cracking/hashcat\_tips.md)
      * [Password Cracking Resources](red-team/credential\_access/brute\_force/password\_cracking/password\_cracking\_resources.md)
    * [Create a Custom Wordlist with Hashcat](red-team/credential\_access/brute\_force/create-a-custom-wordlist-with-hashcat.md)
  * [Password Spraying](red-team/credential\_access/password\_spraying/README.md)
    * [Spray Microsoft](red-team/credential\_access/password\_spraying/spray\_microsoft.md)
  * [OS Credential Dumping](red-team/credential\_access/os-credential-dumping/README.md)
    * [LSA Secrets](red-team/credential\_access/os-credential-dumping/lsa-secrets.md)
* [Lateral Movement](red-team/lateral\_movement/README.md)
  * [WinRM](red-team/lateral\_movement/winrm.md)
  * [Check if your tunnel is active](red-team/lateral\_movement/check\_if\_tunnel\_is\_alive.md)
* [Command and Control](red-team/command-and-control/README.md)
  * [Protocol Tunneling](red-team/command-and-control/protocol-tunneling/README.md)
    * [Using Chisel to Pivot](red-team/command-and-control/protocol-tunneling/using-chisel-to-pivot.md)

## Tools

* [Enumeration](tools/enumeration/README.md)
  * [Nmap](tools/enumeration/nmap/README.md)
    * [Basic Nmap Methodology](tools/enumeration/nmap/basic\_nmap\_methodology.md)
    * [NSE Scripts](tools/enumeration/nmap/nse\_scripts.md)
  * [Enum4Linux](tools/enumeration/enum4linux/README.md)
    * [Grep Usernames](tools/enumeration/enum4linux/grep\_usernames.md)
* [Exploitation](tools/exploitation/README.md)
  * [Responder](tools/exploitation/responder/README.md)
    * [Output In-Scope Hosts from Responder](tools/exploitation/responder/output-inscope\_hosts\_from\_responder.md)
  * [Metasploit](tools/exploitation/metasploit/README.md)
    * [Download Nessus Scan via Metasploit](tools/exploitation/metasploit/download\_nessus\_scan-via\_metasploit.md)
    * [Metasploit Datatabase](tools/exploitation/metasploit/metasploit\_database.md)
  * [Impacket](tools/exploitation/impacket/README.md)
    * [mssqlclient.py](tools/exploitation/impacket/mssqlclient.py.md)
  * [CrackMapExec](tools/exploitation/crackmapexec/README.md)
    * [CrackMapExec Examples](tools/exploitation/crackmapexec/crackmapexec\_examples.md)
* [Web Application](tools/web-application/README.md)
  * [Burp Suite](tools/web-application/burp\_suite/README.md)
    * [Intruder Attack Types](tools/web-application/burp\_suite/intruder\_attack\_types.md)
* [Wireless Testing](tools/wireless-testing/README.md)
  * [Aircrack-ng](tools/wireless-testing/aircrack-ng/README.md)
    * [Aireplay-ng](tools/wireless-testing/aircrack-ng/aireplay-ng.md)
    * [Airmon-ng](tools/wireless-testing/aircrack-ng/airmon-ng.md)
    * [Airodump-ng](tools/wireless-testing/aircrack-ng/airodump-ng.md)

## Resources

* [Penetration Testing Tools](resources/penetration\_testing\_tools.md)
* [Offensive Security Notes](resources/red\_notes.md)
* [Blog Posts and Goodies](Resources/Blog\_Posts\_and\_Goodies.md)

## Miscellaneous

* [Segmentation Testing Notes](miscellaneous/segmentation\_testing\_notes.md)
* [Useful Commands](miscellaneous/useful\_commands.md)
* [Common Troubleshooting](Miscellaneous/Common\_Troubleshooting.md)

## Web Application

* [Remote File Inclusion (RFI)](web-application/remote-file-inclusion-rfi.md)
* [Local File Inclusion (LFI)](web-application/local-file-inclusion-lfi.md)

## OSCP

* [OSCP Must-read Resources](oscp/oscp-must-read-resources.md)
* [Active Directory Methodology](oscp/active-directory-methodology.md)
* [Pre-OSCP Tooling Checklist](oscp/pre-oscp-tooling-checklist.md)
* [OSCP Notes](oscp/oscp-notes.md)
* [Enumeration Checklist](oscp/enumeration-checklist.md)
