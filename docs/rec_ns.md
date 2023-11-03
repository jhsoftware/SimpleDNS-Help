---
Slug: ns-records
Keywords: NS record type,Name server record
DocID: 46
---
# NS-Records (Authoritative name server)

NS-records identify the DNS servers responsible ([authoritative](df_authoritative.md)) for a [zone](df_zones.md).

A [zone](df_zones.md) should contain one NS-record for each of its own DNS servers (primary and secondaries).

This is mostly used for [zone transfer](df_zonetransfer.md) purposes (notify messages).

These NS-records have the same name as the zone in which they are located.

The more important function of the NS-record is delegation.

Delegation means that part of a domain is delegated to other DNS servers.

For example, all ".com" sub-names (such as "example.com") are delegated from the "com" zone.

The "com" zone contains NS-records for all ".com" sub-names (a lot!).

You can delegate sub-names of your own domain name (such as "subname.example.com") to other DNS servers the same way.

To delegate "subname.example.com", create NS-records for "subname.example.com" in the "example.com" zone.

These NS-records must point to the DNS server responsible for "subname.example.com", for example, "ns1.subname.example.com" - or a DNS server somewhere else like "ns1.othername.net".

An NS-record identifies the name of a DNS server - not the IP-address.

Because of this, it is important that an [A-record](rec_a.md) and/or [AAAA-record](rec_aaaa.md) for the referenced DNS server exists (not necessarily on your DNS server, but wherever it belongs), otherwise there may not be any way to connect with that DNS server.

If an NS-record delegates a sub-name ("subname.example.com") to a DNS server with a name in that sub-name ("ns1.subname.example.com"), an [A-record](rec_a.md) / [AAAA-record](rec_aaaa.md) for that server (""ns1.subname.example.com") must exist in the parent zone ("example.com").

This A-record is called a "glue record", because it doesn't really belong in the parent zone, but is necessary to locate the DNS server for the delegated sub-name.

To create a new NS-record, right-click a zone in the left list in the [DNS Records window](wd_records.md), and select "New NS-record" from the pop-up menu.

This record type is defined in [RFC1035](http://www.rfc-editor.org/rfc/rfc1035.txt).
