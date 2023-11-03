---
Slug: ptr-records
Keywords: PTR record type,Reverse record
DocID: 50
---
# PTR-Records (domain name pointer)

PTR-records are primarily used as "reverse records" - to map IP addresses to domain names (reverse of [A-records](rec_a.md) and [AAAA-records](rec_aaaa.md)).

For a reverse IPv4 mapping, the name of the PTR-record is the IP address with the segments reversed and with "in-addr.arpa" appended to the end.

As an example, looking up the domain name for IP address "12.23.34.45" is done with a query for the PTR-record for "45.34.23.12.in-addr.arpa".

For a reverse IPv6 mapping, the name of the PTR-record is each hex digit of the IP address in reverse order, with dots between each digit, and with "ip6.arpa" appended to the end.

As an example, looking up the domain name for IPv6 address "1234:5678:90ab:cdef:1234:5678:90ab:cdef" is done with a query for the PTR-record for "f.e.d.c.b.a.0.9.8.7.6.5.4.3.2.1.f.e.d.c.b.a.0.9.8.7.6.5.4.3.2.1.ip6.arpa".

For more information see the section on [Reverse DNS](df_reverse.md).

To create a PTR-record use one of the following options:

 -  The [Reverse zone IP-to-Name Mappings dialog](wd_iptoname.md).

 -  The "Update Reverse Zone" check box in the [Record Properties dialog](wd_recprop.md) for an A-record or AAAA-record.

 -  Right-click a reverse zone in the [DNS Records window](wd_records.md), and select "New PTR-record" from the pop-up menu.

 This record type is defined in [RFC1035](http://www.rfc-editor.org/rfc/rfc1035.txt).
