---
Slug: how-to-setup-primary-secondary
Keywords: Primary,Secondary
DocID: 23
---
# How to setup primary / secondary

You have a probably come across the terms "primary DNS server" and "secondary DNS server".

Actually a DNS server (the computer/software) is not specifically "primary" or "secondary".

A DNS server can be primary for one [zone](df_zones.md) (domain) and secondary for another.

The DNS specifications (RFCs) require that each domain name is served by at least 2 DNS server for redundancy.

This may seem a little silly - especially if you run your DNS, web, and mail servers all on the same machine - if this machine goes down, it doesn't really matter that the backup DNS server still works.

But many registrars (companies that register domain names) still require at least 2 DNS servers.

This requirement has been somewhat relaxed lately, and depending which registrar you use, you may only need to specify one DNS server.

NOTE: If your registrar lets you use only one DNS server, some DNS testing tools may still flag this as an error.

NOTE: Registrars requiring 2 DNS servers sometimes refer to these as "primary" and "secondary".

This has absolutely nothing to do with the actual primary/secondary functionality, and it doesn't matter in which order you enter your DNS servers for the domain name. This is just a list of servers, and there could be 1, 2, or any number of DNS servers listed for a domain name.

By definition, a primary DNS server holds the "master copy" of the data for a [zone](df_zones.md), and secondary servers have copies of this data which they synchronize from the primary through [zone transfers](df_zonetransfer.md) at intervals or when prompted by the primary.

Only one DNS server should be configured as primary for a [zone](df_zones.md), but you can have any number of secondary servers for redundancy.

Both primary and secondary servers for a [zone](df_zones.md) serve exactly the same data to clients.

Because of this you could easily "simulate" a secondary server on a single computer with 2 IP addresses.

Simply configure the [zone](df_zones.md) (as primary), and the server will function as both the primary (on one IP address) and secondary (on the other IP address).

The recommended practice is to configure the primary and secondary DNS servers on separate machines, on separate Internet connections, and in separate geographic locations (for the purpose of redundancy).

When using separated primary and secondary DNS servers, [zone transfers](df_zonetransfer.md) are used to synchronize the zone data from the primary DNS server to the secondary server(s).

With other DNS server software, a zone must initially be created on both the primary and secondary servers (creating individual DNS records and any subsequent changes to a zone need only be done on the primary server).

However, Simple DNS Plus has a unique option to automatically create and remove zones on secondary servers whenever you do this on the primary.

We call this a "Super Master/Slave" pair and is configured through the [Options dialog / DNS / Local Zones / Super Master/Slave section](wd_opt_dnsms.md).

Both servers must be running Simple DNS Plus (no other DNS servers we know of currently support this).

The secondary server must be listed as a "slave" on the primary server, and the primary server must be listed as a "master" on the secondary.

One Simple DNS Plus server can be master and/or slave for any number of other Simple DNS Plus servers.

To create the [zone](df_zones.md) on the primary server, you can use the [Quick Zone Wizard](wd_quickdom.md).

If you are not using the Super Master/Slave setup, or if either of your DNS servers are not Simple DNS Plus, you will also need to create the [zone](df_zones.md) on the secondary server.

Use the [New Zone](wd_newzone.md) function, select the "Secondary Zone" option, and specify the zone name and the IP address of the primary DNS server.

Once a zone is configured on both primary and secondary servers, [zone transfers](df_zonetransfer.md) should automatically occur when needed.

To verify, use the [Look Up](wd_lookup.md) function against the secondary server, or check the records on the secondary server through the [DNS Records window](wd_records.md) on that server.

You can later change the primary/secondary status using the [Zone Properties dialog](wd_zoneprop.md).

The [Zone Properties dialog](wd_zoneprop.md) "zone transfers" tab can be used to [secure](ht_secure.md) the zone, so only authorized secondary servers are allowed to request [zone transfer](df_zonetransfer.md).
