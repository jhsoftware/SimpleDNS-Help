---
Slug: export-wizard
Keywords: Export Wizard
DocID: 66
---
# Export Wizard

The Export Wizard lets you export data from Simple DNS Plus in four different ways.

For all export options, you can select to export all zones or only the zones in specific zone groups, and whether or not to include suspended zones.

- **Standard boot file and zone files**\
Simple DNS Plus stores zones and records in a proprietary binary format in a single database file (along with other data).\
If you need to move the DNS zones / records to another DNS server, you can use this function to export everything to standard format text files (one zone file for each exported zone and a boot file listing the zones).

- **Standard boot file for secondary DNS server**\
Generates a standard boot file listing primary zones from this server as secondary zones. The generated file can be imported or used directly on a secondary DNS server. Some secondary DNS service providers offer a function to import such a file directly saving a lot of typing.\
NOTE: If you are setting up another Simple DNS Plus server as secondary to this one, we recommend you use the [Super Master/Slave](wd_opt_dnsms.md) feature to synchronize the two servers. This is much easier and will also automatically synchronize any later zone additions and deletions.

- **IP addresses to "hosts" or ".csv" file**\
Scans local zones for host records (A / AAAA) and generates a sorted list of IP address/host name pairs. This can be used to track which IP addresses are in use. The generated "hosts" file could also be used directly for simple name resolution.
