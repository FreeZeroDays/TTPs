---
description: Tips and tricks with NSE scripts
---

# NSE Scripts

### What is NSE?

The Nmap Scripting Engine (NSE) is one of Nmap's most powerful and flexible features. It allows users to write (and share) simple scripts (using the Lua programming language) to automate a wide variety of networking tasks.

TL;DR: NSE goes brrr

### Basic NSE usage

#### List all available NSE scripts

```bash
locate *.nse
```

#### Load default NSE scripts

```bash
nmap -sC [TARGET]
```

#### Specify a specific NSE script

```bash
nmap --script=ssh2-enum-algos -p22 [TARGET]
```

Specify a specific [category](https://nmap.org/book/nse-usage.html)``

```bash
nmap --script discovery,vuln [TARGET]
```

#### Using a wildcard to use multiple relevant scripts (e.g., ssh)

```bash
nmap --script "ssh-*" -p22 [TARGET]
```

### Useful NSE Scripts

This section includes NSE scripts that are not included with Nmap and should be manually added:

* [nndefaccts](https://github.com/nnposter/nndefaccts) - Alternate fingerprint dataset for Nmap script http-default-accounts
* [Nmap-Elasticsearch-NSE](https://github.com/theMiddleBlue/nmap-elasticsearch-nse) - Nmap NSE script for enumerating indices, plugins and cluster nodes on an elasticsearch target

## References

* [NSE-Usage](https://nmap.org/book/nse-usage.html)
