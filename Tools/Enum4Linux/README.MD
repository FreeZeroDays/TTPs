# Enum4Linux

Enum4linux is a tool for enumerating information from Windows and Samba systems.

## Installation 

Install Enum4Linux with git: 

```git clone https://github.com/CiscoCXSecurity/enum4linux```

## Usage

Enumerate users on the target host \
```enum4linux -U [TARGET]```

Enumerate SMB shares on the target host \
```enum4linux -S [TARGET]```

Enumerate the password policy \
```enum4linux -P [TARGET]```

Enumerate operating system information \
```enum4linux -o [TARGET]```

If the target is a domain controller you can enumerate some information from LDAP \
```enum4linux -l [TARGET]```

Identify if any printers are connected to our target \
```enum4linux -i [TARGET]```

## References
* [Enum4Linux](https://www.kali.org/tools/enum4linux/)
