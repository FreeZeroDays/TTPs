# Check if your tunnel is active

**Description:** Commands to run to veiryf if your SSH tunnel is active and running successfully:

Check tunnel with netcat:

```nc -z localhost [PORT] || echo "no tunnel open"```

Check tunnel with netstat:

```netstat -lpnt | grep [PORT] | grep ssh```

Check tunnel with ps: 

```ps aux | grep ssh```
