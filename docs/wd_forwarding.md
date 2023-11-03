---
Slug: dns-forwarding-dialog
Keywords: Forwarding
DocID: 67
---
# DNS Forwarding dialog

- **Forward DNS requests for**\
Specify which domain names to forward DNS requests for.\
Forwarding for only a specific domain name (and sub-names) is also know as "conditional forwarding".

- **To DNS servers**\
Specify the IP addresses of the DNS servers to forward these DNS requests to.

- **Enable Extended Forwarding**\
Also forward non-recursive DNS requests and DNS requests originating from IP addresses that are not offered recursion.\
(Standard DNS forwarding only forwards [recursive](df_recursion.md) DNS requests from IP addresses [offered recursion](wd_opt_dnsrecur.md))

 - **Enable Shadow Forwarding**\
Also forward DNS requests for the name or sub-name of a local DNS zone when no matching DNS records exist in that zone.\
(Standard DNS forwarding only forwards request which are not for the name or sub-name of a local DNS zone)\
In the "Authoritative Answer (AA) flag" dropdown, specify if the AA-flag in the response should be set or cleared.

See also: [Forwarding](df_forward.md)
