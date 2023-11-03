---
Slug: aaaa-records
Keywords: AAAA record type,IPv6 host address,Host address
DocID: 31
---
# AAAA-Records (IPv6 host address)

An AAAA-record is used to specify the IPv6 address for a host (equivalent of the [A-record](rec_a.md) type for IPv4).

IPv6 is the new replacement for the old IPv4 address system.

IPv4 addresses are 32 bits long ( x . x . x . x = 4 bytes), and therefore "only" support a total of 4,294,967,296 addresses - less than the global population.

The Internet ran out of IPv4 addresses in 2019, and to solve the problem, the whole Internet will eventually be migrated to IPv6.

IPv6 addresses are 128 bits long and are written in hexadecimal numbers separated by colons (:) at every four digits (segment).

A series of zero value segments can be shortened as "::", and leading zeros in a segment can be skipped.

For example: 4C2F::1:2:3:4:567:89AB.

To create a new AAAA-record, right-click a zone in the left list in the [DNS Records window](wd_records.md), and select "New AAAA-record" from the pop-up menu.

This record type is defined in [RFC3596](http://www.rfc-editor.org/rfc/rfc3596.txt).
