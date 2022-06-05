# Cracking the Handshake

### Description

This page assumes you have already collected the authentication handshake. If not, please reference [wifite2](wifite2.md).

### Hashcat

> Use hash mode 22000 to recover a Pre-Shared-Key (PSK). Length of a PSK can be 8 up to 63 characters

```bash
hashcat -m 22000 $handshake /usr/share/wordlists/rockyou.txt -w /usr/share/rules/OneRule.rule
```

### Aircrack-ng

```bash
aircrack-ng -w /usr/share/wordlists/rockyou.txt $capture.cap
```
