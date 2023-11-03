---
Slug: options-dialog-dns-local-zones-super-masterslave
Keywords: Master,Slave,Super Master,Super Slave
DocID: 79
---
# Options dialog - DNS - Local Zones - Super Master/Slave

The Super Master/Slave feature is used to automatically create and remove zones on secondary (slave) servers.

When you create a new primary zone on the master server, all slave servers (the "Super Slaves" list on the master server) will be notified that there is now a new zone available. When a slave server receives such a notification, it first checks its master list (those listed in "Super Masters") to validate the master, then requests update information and creates the zone (as secondary).

A similar process happens when you delete a zone from the master server.

A Simple DNS Plus server can act as both master (primary zones) and slave (secondary zones) at the same time, and can have multiple masters and slaves.

- **Super Slaves**

    - **The following DNS servers are secondary for all primary zones on this server**\
    List of slave server IP addresses.

    - **Accept un-signed zone transfer requests from above IP addresses**\
    Unless this option is checked, slave servers must [TSIG sign](df_tsig.md) zone transfer requests including zone list synchronization requests.\
    The acceptable TSIG keys for such signed requests are specified on the in the [Zone Transfers section](wd_opt_dnszt.md).

- **Super Masters**

    - **This server is secondary for all primary zones on the following DNS servers**\
    List of master server IP addresses.\
    A TSIG key for signing zone transfer and zone list synchronization requests can optionally be specified for each master server.

    - **Bulk refresh / verify zone lists every**\
    Simple DNS Plus retrieves a list of zones and their current serial numbers from the DNS servers in the Super Masters list (above) at this interval.\
    It uses this list to synchronize both individual zones and the zone list.\
    If you have a lot of zones (thousands) you may want to enforce long "Refresh" values on secondary zones (see [Secondary Zones section](wd_opt_dnsns2.md)) in order to reduce synchronization traffic between the DNS servers.\
    Even with long "Refresh" values, secondary servers will still get zone updates almost immediately as they happen on the primary server because the primary server will send it a NOTIFY message (make sure to enable "Send NOTIFY..." in the [Miscellaneous section](wd_opt_dnsmisc.md) on the master).\
    If you set this (Bulk refresh / verify zone lists every) to a slightly shorter value than the enforced "Refresh" value, the effect is that all secondary zones will be refreshed in a single operation at this interval, and never get around to refreshing individually. This is obviously much more efficient.


**NOTE:** This functionality (super master/slave) is unique to Simple DNS Plus, and is not currently supported by other DNS server implementations, so both master and slave must be running Simple DNS Plus.

**NOTE:** In earlier versions of Simple DNS Plus, this feature was called "Master/Slave" (without "Super").\
This function has been improved in recent versions of Simple DNS Plus, but the main reason for adding "Super" was that new users often thought that "Master/Slave" was just different terminology for "Primary/Secondary" and therefore didn't realize the full potential of this function.\
"Super Master/Slave" is fully compatible with "Master/Slave" in earlier versions.



See also: [Zone Transfer](df_zonetransfer.md), [TSIG Signature](df_tsig.md)
