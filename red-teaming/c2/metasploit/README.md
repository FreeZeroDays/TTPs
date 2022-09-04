# Metasploit

```bash
# Installing the Metasploit Framework
curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall && chmod 755 msfinstall && ./msfinstall
```

### Basic Usage

```bash
# Access msfconsole
./msfconsole

# Enable and start the database
msfdb init

# Delete and reinit the database
msfdb reinit

# Stop the database
msfdb stop

# Delete the database
msfdb delete
```

### References

{% embed url="https://docs.rapid7.com/metasploit/msf-overview/" %}
