---
description: MITRE ATT&CK, Credential Access, Technique T1552
---

# Unsecured Credentials

### Finding Credentials with MANSPIDER

```bash
# MANSPIDER installation:
sudo apt install tesseract tesseract-data-eng antiword pip install pipx pipx install man-spider

# Regex search for the following variables:
manspider.py $ip -d $domain -u $user -p $password -f passw user admin account network login logon cred

# Regex search in XLSX files:
manspider.py $target -d $domain -u $user -p $password -c password -e xlsx

# Perform a search by passing the hash of a user:
manspider.py $target -d $domain -u $user -H $hash -f passw user admin account network login logon cred
```

{% embed url="https://github.com/blacklanternsecurity/MANSPIDER" %}

### Hunting with SMBEagle

```bash
# Hunt for shares and scan the domain SMBEagle fast mode
./SMBeagle.exe -c out.csv -f
```

{% embed url="https://github.com/punk-security/smbeagle" %}

###

### References

{% embed url="https://www.sprocketsecurity.com/blog/how-to-limit-cleartext-password-storage-and-fix-the-issue-in-your-organization" %}
