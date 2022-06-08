---
description: >-
  Commands to run to verify if your SSH tunnel is active and running
  successfully after establishing a session
---

# Check if SSH Tunnel is Active

#### Check tunnel with netcat:

```bash
nc -z localhost $port || echo "no tunnel open"
```

#### Check tunnel with netstat:

```bash
netstat -lpnt | grep $port | grep ssh
```

#### Check tunnel with ps:

```bash
ps aux | grep ssh
```
