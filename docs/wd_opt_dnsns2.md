---
Slug: options-dialog-dns-local-zones-secondary-zones
Keywords: Secondary,Secondary Zones,Incremental zone transfer,IXFR
DocID: 81
---
# Options dialog - DNS - Local Zones - Secondary Zones

- **Maximum refresh / IXFR requests to send per second**\
On servers with many secondary zones, this settings prevents flooding primary DNS servers with refresh / IXFR (incremental [zone transfer](df_zonetransfer.md)) requests.

- **Maximum parallel zone transfers (From different primary servers)**\
Limits the number of simultaneous TCP zone transfer connections made to primary servers.\
NOTE: Simple DNS Plus will never establish more than one TCP zone transfer connection to any one primary DNS server at a time (based on IP address). Therefore this setting has no effect if all secondary zones come from the same primary server.

- **Retry transferring expired zones every**\
This value controls how often the server will attempt to retrieve zone data for expired secondary zones from their primary DNS server (zone transfer). Expired zones include new (never zone transferred) secondary zones.

- **Use incremental zone transfers (IXFR)**\
Incremental zone transfers are generally more efficient than full zone transfers.
However it may be necessary or more efficient to disable this setting if your primary DNS server does not support IXFR.

- **Only accept NOTIFY requests from IP address of primary DNS server**\
Whenever a [zone](df_zones.md) is updated, the primary DNS server will send a NOTIFY request to secondary DNS servers for the zone to let them know about the update (assuming this is enabled on the primary DNS server - see [Miscellaneous section](wd_opt_dnsmisc.md)).\
The secondary DNS servers will then refresh the zone and request a new copy of the data by [zone transfer](df_zonetransfer.md) if necessary.\
With this option enabled, such NOTIFY requests will only be accepted if they originate from the IP address that is configured as the primary DNS server IP address for the zone. This prevents stray or malicious requests from triggering the zone refresh process.\
NOTE: If the primary DNS server is multi-homed (more than one IP address), NOTIFY requests could originate from a different IP address.\
In Simple DNS Plus, the IP address that outbound requests (including NOTIFY requests) are sent from is configured in the [Options dialog / DNS / Outbound requests](wd_opt_dnsout.md) section.

- **Enforce minimum values for secondary zone SOA records**\
Can be used to limit the number of refresh and zone transfer requests.\
Recommended if you don't control the primary DNS server for the secondary zones you host.
