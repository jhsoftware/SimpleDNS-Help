---
Slug: bulk-update-wizard
Keywords: Find and replace IP,Replace IP,Promote server,Bulk Update Wizard
DocID: 60
---
# Bulk Update Wizard

Use this wizard to quickly update many zones in a single operation.

For all update options, you can select to update all zones or only the zones in specific zone groups.

- **Find and replace IP address**\
Replaces an IP address in host records ([A-records](rec_a.md) for IPv4 addresses / [AAAA-records](rec_aaaa.md) for IPv6 addresses)\
Use this option, for example, when changing the IP address of a server hosting web-sites or other services for several different domain names.\
You must enter the old IP address and the new IP address of the server.

- **Find and replace host name**\
Use this option to replace a host name in the data part of [CNAME](rec_cname.md), [MX](rec_mx.md), [NS](rec_ns.md), [PTR](rec_ptr.md), RT, [SOA](rec_soa.md), and [SRV](rec_srv.md) records.\
You must enter the old host name and the new host name, and select which record types to update.

- **Update DNS record TTL (Time To Live) values**\
Use this option to update DNS record [TTL](df_ttl.md) values.\
You must enter the new TTL value and select which record types to update.

- **Update zone e-mail servers (MX-records)**\
Use this option to replace zone level [MX-records](rec_mx.md) (MX-records for sub-names will not be updated).\
You can enter up to 5 different e-mail server host names and their preference values.

- **Update DNS servers ([NS-](rec_ns.md) and [SOA-records](rec_soa.md))**\
Use this option, for example, when you add or change a DNS server hosting all of your domain names.\
You must enter the primary DNS server name and up to 4 secondary DNS server names.

- **Update SOA-record data field values**\
Use this option to update individual [SOA-record](rec_soa.md) data fields.\
You can select which data fields to update and which to leave at their current value.

- **Promote secondary zones to primary zones**\
Use this option, for example, if your primary DNS server is permanently down/gone and you wish this secondary DNS server to become the new primary DNS server.\
You must select what to do about secondary zones which have already expired (create empty primary zone, leave as secondary, or delete).

- **Update primary DNS server IP address for secondary zones**\
Use this option on your secondary DNS servers when the IP address of your primary DNS server has changed in order to quickly update all your secondary zones.\
You must specify the current primary DNS server IP address and the new primary DNS server IP address.
