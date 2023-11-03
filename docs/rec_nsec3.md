---
Slug: nsec3-records
Keywords: NSEC3 record type
DocID: 48
---
# NSEC3-Records (Next Secure v. 3)

An NSEC3-record links to the next record name in the [zone](df_zones.md) (in hashed name sorting order) and lists the record types that exist for the name covered by the hash value in the first label of the NSEC3 -record's own name.

These records can be used by resolvers to verify the non-existence of a record name and type as part of [DNSSEC](df_dnssec.md) validation.

NSEC3-records have the same functionality as [NSEC-records](rec_nsec.md), except NSEC3 uses cryptographically hashed record names to prevent enumeration of the record names in a zone.

NSEC3-records have the following data elements:

- Hash Algorithm: The cryptographic hash algorithm used.

- Flags: "Opt-out" (indicates if delegations are signed or not).

- Iterations: How many times the hash algorithm is applied.

- Salt: Salt value for the hash calculation.

- Next Hashed Owner Name: The name of the next record in the zone (in hashed name sorting order).

- Record Types: The record types that exist for the name covered by the hash value in the first label of the NSEC3 -record's own name.

To add NSEC3-records to a zone, use the [DNSSEC Sign Zone](wd_signzone.md) function.

This record type is defined in [RFC5155](http://www.rfc-editor.org/rfc/rfc5155.txt).
