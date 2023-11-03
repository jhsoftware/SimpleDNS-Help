---
Slug: options-dialog-dns-resolver-ip-filtering
Keywords: Response filtering,DNS rebinding attack
DocID: 86
---
# Options dialog - DNS - Resolver - IP Filtering

- **Remove host records (A/AAAA) containing the following IP addresses from responses received from other DNS servers**\
When this option is enabled, hosts records with the IP addresses listed will be removed from responses.

- **Trusted DNS servers - host records will NOT be removed from responses from DNS servers with these IP addresses**\
IP addresses of trusted DNS servers.


**How to use this:**

This function is primarily intended to prevent [DNS rebinding attacks](ht_secure.md#rebinding) - it can however also be used to filter out undesirable IP addresses in general.
