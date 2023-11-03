---
Slug: definition-authoritative
Keywords: Authoritative
DocID: 1
---
# Definition - Authoritative

A DNS server is said to be authoritative for a domain name when it hosts the DNS records for that domain name.

An authoritative DNS server for a domain name is configured with a local DNS [zone](df_zones.md) for the domain name and its sub-names.

Both the primary and the secondary DNS servers for a domain name are considered authoritative.

An authoritative DNS server for a domain name responds with "Authoritative Answers" for the domain - as indicated by the "AA" header flag set in responses.
