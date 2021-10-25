# Check if your tunnel is active

**Description:** Commands to run to veirfy if your SSH tunnel is active and running successfully after establishing a session:

Check tunnel with netcat: \

```nc -z localhost [PORT] || echo "no tunnel open"```

Check tunnel with netstat: \

```netstat -lpnt | grep [PORT] | grep ssh```

Check tunnel with ps: \

```ps aux | grep ssh```
