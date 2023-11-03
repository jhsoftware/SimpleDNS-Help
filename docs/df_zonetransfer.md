---
Slug: definition-zone-transfer
Keywords: Zone Transfers,Synchronize
DocID: 17
---
# Definition - Zone Transfer

A primary DNS server has the "master copy" of a [zone](df_zones.md), and secondary DNS servers keep copies of the [zone](df_zones.md) for redundancy.

When changes are made to zone data on the primary DNS server, these changes must be distributed to the secondary DNS servers for the zone.

This is done through zone transfers.

Most DNS servers automatically notifies secondary servers whenever changes are made through a NOTIFY request, and most DNS servers will request a Zone Transfer whenever such a notification is received.

You can specify if Simple DNS Plus should send these NOTIFY requests to secondary DNS servers in the [Options dialog / DNS / Miscellaneous section](wd_opt_dnsmisc.md).

For this to work correctly, [NS-records](rec_ns.md) and corresponding [A-records](rec_a.md) for each secondary DNS server must exist in the [zone](df_zones.md).

Secondary servers also periodically check for changes by querying the primary server for the [SOA-record](rec_soa.md) of the [zone](df_zones.md), and checking the serial number.

In addition to whatever other changes are made to a zone and its records, the serial number of the [SOA-record](rec_soa.md) must always be incremented.

NOTE: Simple DNS Plus does this for you automatically as long as you do not change the serial number yourself.

The periodic polling by the secondary servers is controlled by the refresh, retry, and expire parameters of the [SOA-record](rec_soa.md).

The secondary server waits for the "refresh" interval before checking with the primary for a new serial number. If this check cannot be completed, new checks are started every "retry" interval.

If the secondary finds it impossible to perform a serial check within the "expire" interval, it discards the zone.

When the poll shows that the zone has changed (higher serial number), the secondary server will fetch a fresh copy of the zone through a zone transfer request.

A standard (full) zone transfer transfers all the records in the zone from the primary to the secondary server.

Simple DNS Plus also supports an optimized "incremental zone transfer" method which saves bandwidth by only transferring changes made since the last zone transfer, and by using UDP packets instead of TCP.

By default Simple DNS Plus will request incremental zone transfers when getting zone updates. If the primary server does not support this and returns an error, Simple DNS Plus will then revert to doing a full zone transfer.

If you know that your primary DNS server does not support incremental zone transfers, you can prevent Simple DNS Plus from using this with a setting in the [Options dialog / DNS / Local Zones / Secondary Zones section](wd_opt_dnsns2.md).

Simple DNS Plus does not allow zone transfer requests by default because this could be used by hackers to lists all your servers etc. and thus give them a list of potential targets.

You obviously have to configure your primary DNS server to accept zone transfer requests from your secondary DNS server(s).

This can be done by using [TSIG signatures](df_tsig.md) or by configuring which IP addresses to accept un-signed zone transfer requests from, either in the [Zone Properties dialog](wd_zoneprop.md) for each individual [zone](df_zones.md), or in the [Options dialog / DNS / Local Zones / Zone Transfers section](wd_opt_dnszt.md) for all zones.

Using TSIG signatures is more secure and is recommend over limiting access by IP address, because IP addresses can be spoofed. Incremental zone transfers over UDP are particularly vulnerable to IP address spoofing.

See also: [How to setup primary / secondary](ht_primsec.md)
