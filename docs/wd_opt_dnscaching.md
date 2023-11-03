---
Slug: options-dialog-dns-resolver-caching
Keywords: Caching,Minimum cache time,Maximum cache time
DocID: 75
---
# Options dialog - DNS - Resolver - Caching

- **Cache DNS records received in responses from other DNS servers**\
Use this option the enable/disable [caching](df_cache.md)

    - **Maximum cache time**\
    By default, records are removed from the cache based on the TTL received from the original DNS server.\
    These settings specify the maximum amount of time DNS records are cached.

    - **Maximum DNS records cached**\
    You can use this option to limit the amount of memory Simple DNS Plus will use for caching.

    - **Override low TTL values / Minimum cache time / TTL**\
    WARNING: This option should NOT be enabled by most users.\
    Enabling this will likely cause problems with many domain names that rely on frequent DNS updates either because they use dynamic IP addresses or some type of DNS based load balancing or failover system.\
    "cnn.com" is one example of a larger web site, which depends on low TTL values to enable quick changes to their web site (they currently use DNS TTL values of 5 minutes).\
    Many smaller web-sites also depend on low TTL values because they run on dynamic IP addresses and therefore require frequent DNS updates (when their IP address changes).\
    There are however special situations such as Internet connections with high latency (satellite connections for example) where it may make sense to trade DNS accuracy for faster DNS lookups.

    - **Store cached DNS records on disk between shutdown/startup**\
    If this option is checked, all cached records are written to disk when Simple DNS Plus is closed (including when the computer is shut down correctly).\
    When Simple DNS Plus is later restarted, it will reload the cache recalculating the DNS records' [TTLs](df_ttl.md) based on the time the program was closed.



See also: [Caching](df_cache.md), [TTL](df_ttl.md)
