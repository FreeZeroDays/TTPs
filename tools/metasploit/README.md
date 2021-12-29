---
description: >-
  The Metasploit Framework is a Ruby-based, modular penetration testing platform
  that enables you to write, test, and execute exploit code.
---

# Metasploit

### Installation

Install the Metasploit Framework on Linux \
`curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall && chmod 755 msfinstall && ./msfinstall`

### Basic Usage

Access the MSFconsole on Linux \
`./msfconsole`

Enable and start the database \
`msfdb init`

Show the status of the database \
`msfdb status`

Delete and reinitialize the database \
`msfdb reinit`

Stop the database \
`msfdb stop`

Delete the database \
`msfdb delete`

### References

* [Metasploit Documentation](https://docs.rapid7.com/metasploit/msf-overview/)
