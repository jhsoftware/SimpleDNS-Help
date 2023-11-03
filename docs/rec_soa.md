---
Slug: soa-records
Keywords: SOA record type,Start of authority,Serial number,Refresh interval,Retry interval,Expire interval,Minimum TTL
DocID: 53
---
# SOA-Records (Start of authority)

A [zone](df_zones.md) contains exactly one SOA-record, which holds the following properties for the zone:

 - **Name of primary DNS server**

    The host name of the primary DNS server for the zone.

    The zone should contain a matching [NS-record](rec_ns.md).

    NOTE: For dynamic updates from Windows clients and Active Directory to work correctly, it is important that this contains the correct host name for the primary DNS server for the zone, and also that an A-record exists for this name pointing to the correct IP address.

 - **E-mail address of responsible person**

    The e-mail address of the person responsible for the zone.

    The standard for this is the "hostmaster" alias - such as "hostmaster@example.com".

 - **Serial number** (see [Zone Transfers](df_zonetransfer.md))

    Used by secondary DNS servers to check if the zone has changed.

    If the serial number is higher than what the secondary server has, a [zone transfer](df_zonetransfer.md) will be initiated.

    This number is automatically increased by Simple DNS Plus when changes are made to the zone or its records (happens when you save the zone).

    Unless you have a specific reason for changing this number, it is best to let Simple DNS Plus manage it.

    You should never decrease a serial number.

 - **Refresh Interval** (see [Zone Transfers](df_zonetransfer.md))

    How often secondary DNS servers should check if changes are made to the zone.

 - **Retry Interval** (see [Zone Transfers](df_zonetransfer.md))

    How often secondary DNS server should retry checking if changes are made - if the first refresh fails.

 - **Expire Interval** (see [Zone Transfers](df_zonetransfer.md))

    How long the zone will be valid after a refresh.

    Secondary servers will discard the zone if no refresh could be made within this interval.

 - **Minimum (default) TTL**

    Used by other DNS servers to [cache](df_cache.md) negative responses (such as record does not exist etc.).

A SOA-record is automatically created when you create a [new zone](wd_newzone.md).

This record type is defined in [RFC1035](http://www.rfc-editor.org/rfc/rfc1035.txt).
