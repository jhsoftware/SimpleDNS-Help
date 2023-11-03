---
Slug: definition-domains-vs-zones
Keywords: Zones
DocID: 16
---
# Definition - Domains vs. Zones

Domains are broken into zones for which individual DNS servers are responsible.

A "domain" represents the entire set of names / machines that are contained under an organizational domain name.

For example, all domain names ending with ".com" are part of the "com" domain.

A "zone" is a domain less any sub-domains delegated to other DNS servers (see [NS-records](rec_ns.md)).

A DNS server could be responsible ([authoritative](df_authoritative.md)) for all records under the "xyz.com" domain, but by defining [NS-records](rec_ns.md) for "abc.xyz.com", this part of the domain is delegated to other DNS servers - and possibly a different company/entity.

A zone contains exactly one [SOA-record](rec_soa.md) describing the general properties of the zone, and any number of other DNS records.

Entire zones can transferred from a primary DNS server to secondary DNS servers through [Zone Transfers](df_zonetransfer.md).

To create a new zone use the [New Zone](wd_newzone.md) function by clicking the "New" button in the [DNS Records window](wd_records.md).
