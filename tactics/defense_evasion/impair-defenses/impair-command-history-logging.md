---
description: MITRE ATT&CK, Defense Evasion, Sub-technique T1562.003
---

# Impair Command History Logging

Impairing command history logging allows for an attacker to operate on a compromised host while leaving minimal evidence behind.&#x20;

### Methods for Linux and MacOS

#### Clearing the HISTFILE

```bash
# Clear the command history variable
unset HISTFILE

# Set the command history size to zero
export HISTFILESIZE=0

# Configure the HISTCONTROL variable to ignore commands that begin with a space. 
HISTCONTROL=ignoreboth
```

### Methods for Windows

```powershell
# Disable the PSReadLine module
Set-PSReadlineOption -HistorySaveStyle SaveNothing

# Modify where logs are stored
Set-PSReadLineOption -HistorySavePath {File Path}
```

### References

{% embed url="https://attack.mitre.org/techniques/T1562/003/" %}
