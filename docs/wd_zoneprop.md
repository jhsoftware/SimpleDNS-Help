---
Slug: zone-properties-dialog
Keywords: SOA record,Zone transfers,Dynamic updates,Zone Properties,DNSSEC
DocID: 107
---
# Zone Properties Dialog

- **General**

    - **Role of this DNS server for this zone**\
    Specify primary or secondary.\
    If primary, specify the default [TTL](df_ttl.md) for new DNS records in the zone.\
    If secondary, specify the IP address of the primary DNS server to [zone transfer](df_zonetransfer.md) the zone from, and optionally the [TSIG](df_tsig.md) key to sign [zone transfer](df_zonetransfer.md) requests with.

    - **Account-ID (optional - for tracking domain name owner or similar)**\
    To track the domain name owner or similar.
    This is primarily intended for use with the HTTP API - allowing you to filter the zone list by account (GET /zones?account=xxx).

    - **Zone Group** (only visible if zone folders are enabled from the View menu)\
    Which zone group/folder the zone belongs to.
    
- **Zone Transfers** (see [How to secure your server](ht_secure.md))\
Specify which IP addresses are allowed to obtain this zone through [zone transfers](df_zonetransfer.md) (typically secondary DNS servers).\
Click the "Add IP addresses of zone's NS-records" button to automatically resolve and add IP addresses of zone level [NS-records](rec_ns.md).

- **Notify**\
Specify which secondary DNS servers to notify when the zone has been updated on the primary server. 

- **Dynamic Updates**\
Specify which IP addresses to accept standard (un-signed) dynamic update requests from for this zone (typically computers on the local network).\
IMPORTANT: Standard dynamic updates should only be used in a secure environment such as a private network.\
For updates sent over the Internet we recommend using [TSIG signed](df_tsig.md) dynamic updates. You can configure this in the [Options dialog / DNS / Local Zones / TSIG Updates section](wd_opt_dnstsig.md).

- **DNSSEC**

    For details on how these settings work - see [DNSSEC](df_dnssec.md).

    - **Automatically DNSSEC sign zone whenever DNS records are updated**
    
        When checked, the zone will automatically be signed whenever needed.
        
        - **...and again every __ days**\
        Specify how often the zone should be signed when there are no record updates.

        - **Signatures expire after __ days**\
        How long signatures are valid for.

        - **Generate a new ZSK every __ days**\
        Automatic ZSK rollover.

            - **Algorithm**\
                Specify the algorithm to use for calculating signatures.

            - **Key size (bits)**\
                Specify the key strength.

            - **Schedule previous ZSK(s) to be deleted __ days later**\
            Whenever a new ZSK is added automatically, all existing ZSKs are scheduled for deletion this number of days later.

    - **Use NSEC3**\
        When checked, NSEC3-records will be used instead of NSEC-records. See [DNSSEC](df_dnssec.md) for details.
    
        - **Salt length**\
        Length of random salt value used in calculation of NSEC3 record-names.
    
        - **Iterations**\
        The number of times NSEC3 record-names are hashed.\
        Note that while using multiple iteration increases security, it also puts additional load on the DNS server serving the zone because it has to calculate this for every single DNS request for non-existing records.

    - **On-line keys...**\
    Click this button to edit the on-line keys for the zone - using the [DNSSEC Keys dialog](wd_dnsseckeys.md).


- **Comments**\
This is an open text area that can contain and comments or additional information about the zone that you need.\
For example information about when the domain expires etc.\
For new zones, Simple DNS Plus will automatically enter a comment about how and when the zone was created.\
NOTE: This information is not automatically transferred to secondary servers through [zone transfers](df_zonetransfer.md).
