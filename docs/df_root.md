---
Slug: definition-root-dns-records
Keywords: Root DNS Records
DocID: 11
---
# Definition - Root DNS Records

At the top of the domain name hierarchy is the root domain (typically written as a single dot or as \<root\>). Information about this domain resides on root servers located around the world.

All Internet DNS servers are configured with references to these root servers referred to as the "root file", "hints file" or "cache file".

Below the root domain are the top-level domains (TLDs), which are either country specific or generic. Examples of country specific top-level domains are SG (Singapore) and CA (Canada), while generic top-level domains include the well-known COM (commercial organizations), EDU (educational institutions), GOV (governmental organizations), and NET (network organizations), among others. 

Below the top-level domains are the second-level domains (whitehouse.gov, microsoft.com, simpledns.plus), and then the third-level domains, and so on.

To locate any domain name, a DNS server starts by asking one of the root servers (unless it already has a closer match [cached](df_cache.md))

The root server will supply a referral ([NS-records](rec_ns.md)) to DNS servers responsible for the next level (.com, .net, etc.).

The DNS server then repeats the request to one of those server, which will supply a referral to DNS servers for the next level (for example; simpledns.plus), and so on, until the requested domain name is found.

This process is know as [recursion](df_recursion.md).

This way a DNS server can locate any name in the world, as long as it knows the IP addresses of the root DNS servers.

Simple DNS Plus includes the standard root file (a.k.a. "hints file") "named.root" containing records for the current Internet root DNS servers. This file is automatically loaded at startup.

Simple DNS Plus can automatically check for root file updates to keep it current - see [Options dialog / DNS / Miscellaneous section](wd_opt_dnsmisc.md).
