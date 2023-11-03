---
Slug: options-dialog-dns-local-zones-zone-transfers
Keywords: Zone transfers
DocID: 89
---
# Options dialog - DNS - Local Zones - Zone Transfers

- **Accept TSIG authenticated zone transfer requests signed with one of the following keys for any zone on this server (from any IP address)**\
Secondary DNS servers [signing](df_tsig.md) zone transfer requests with one of these keys may [zone transfer](df_zonetransfer.md) any zone on this server.\
Zone transfer permissions can also be specified for each individual zone in the [Zone Properties](wd_zoneprop.md) dialog. However the zone transfer requests signed with the keys listed here are always accepted no matter what the settings are in the individual zones.

- **Accept un-signed zone transfer requests for any zone on this server**\
The IP addresses listed here are allowed to request [zone transfers](df_zonetransfer.md) for any zone hosted on this server.\
Zone transfer permissions can also be specified for each individual zone in the [Zone Properties](wd_zoneprop.md) dialog. However the IP addresses listed here can always zone transfer no matter what the settings are in the individual zones.

- **Send only one DNS record per message (older BIND secondary servers)**\
This option should only be enabled if one or more of the zones on the server has an old BIND server as secondary which doesn't understand zone transfer messages with multiple DNS records.\
Note: Enabling this does not prevent newer secondary DNS servers from zone transferring. It will just be less efficient.
