---
Slug: nsec-records
Keywords: NSEC record type
DocID: 47
---
# NSEC-Records (Next Secure)

An NSEC-record links to the next record name in the [zone](df_zones.md) (in [DNSSEC](df_dnssec.md) sorting order) and lists the record types that exist for the record's name.

These records can be used by resolvers to verify the non-existence of a record name and type as part of DNSSEC validation.

NSEC-records have the following data elements:

- Next domain name: The next record name in the zone (DNSSEC sorting order)

- Record types: The DNS record types that exist for the name of this NSEC-record.

To add NSEC-records to a zone, use the [DNSSEC Sign Zone](wd_signzone.md) function.

This record type is defined in [RFC4034](http://www.rfc-editor.org/rfc/rfc4034.txt).
