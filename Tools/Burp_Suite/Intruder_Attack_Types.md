# Intruder Attack Types

**Description:** Brief descriptions of each attack type in Burp Suite Intruder.

## Sniper

Only one payload set needs to be defined. This attack type is useful for fuzzing a number of request parameters individually for common vulnerabilities or for performing a brute-force attack against a single account.

## Battering Ram

This uses a single set of payloads. It will place the payload into all of the defined payload positions at the same time. \
I have not found this to be useful during network penetration tests.

## Pitckfork

This attack runs through all payload sets simultaneously, and places one payload into each position. This attack is great when performing attacks such as credential stuffing against a login form.

## Cluster bomb

This attack iterates through each payload set in turn, so that all permutations of payload combinations are tested. This attack is great when targeting several accounts for a brute-force attack or when performing password spraying against an org. 

## References
* [Burp Suite Payload Positions](https://portswigger.net/burp/documentation/desktop/tools/intruder/positions)
