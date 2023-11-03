---
Slug: default-zone-values-dialog
Keywords: Default Zone Values
DocID: 62
---
# Default Zone Values dialog

Use this dialog to specify default values for all new zones.

Most of these values correspond directly to values in the [Zone Properties dialog](wd_zoneprop.md).

- **SOA-record**\
Specify the default values for new zone [SOA-records](rec_soa.md).

- **Secondary DNS servers**\
Specify the default secondary DNS servers for new zones.\
An [NS-record](rec_ns.md) for each of these will automatically be created in new zones.

- **Zone Transfers**\
Specify the IP addresses that will be allowed to zone transfer (un-[signed](df_tsig.md)) new zones by default.\
This should typically be the same as the secondary DNS servers.\
Use the "Add IP addresses of secondary DNS servers" button to automatically resolve the secondary DNS servers (previous tab) and add their IP addresses to this list.

- **Notify**\
Specify which secondary DNS servers to notify when the zone has been updated on the primary server. 

- **Default TTL**\
Specify the initial default TTL value for new zones.
