---
description: >-
  Collection of Bug Bounty tips & tricks I have discovered and/or read on
  Twitter.
---

# Bug Bounty Tips & Tricks

1. When crawling a target and observing the "node\_modules" directory, make sure to verify each one of those modules being used has a public namespace associated with it (dependency confusion).
   1. [https://snyk.io/blog/detect-prevent-dependency-confusion-attacks-npm-supply-chain-security/](https://snyk.io/blog/detect-prevent-dependency-confusion-attacks-npm-supply-chain-security/)
2. Leverage `xmlrpc.php` with the `pingback.ping` command to discover a sites Origin IP address. Then supply it in the `Host:` header to bypass an in place rate limit.
3.



### References

{% embed url="https://twitter.com/ArchAngelDDay/status/1661924038875435008" %}
