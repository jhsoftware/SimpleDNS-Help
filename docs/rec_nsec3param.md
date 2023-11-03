---
Slug: nsec3param-records
Keywords: NSEC3PARAM record type
DocID: 49
---
# NSEC3PARAM-Records (NSEC3 Parameters)

An NSEC3PARAM-record is used by authoritative DNS servers to calculate and determine which [NSEC3-records](rec_nsec3.md) to include in responses to [DNSSEC](df_dnssec.md) requests for non-existing names/types.

NSEC3PARAM-records have the following data elements:

- Hash Algorithm: The cryptographic hash algorithm used.

- Flags: "Opt-out" (indicates if delegations are signed or not).

- Iterations: How many times the hash algorithm is applied.

- Salt: Salt value for the hash calculation.

To add an NSEC3PARAM-record to a zone, use the [DNSSEC Sign Zone](wd_signzone.md) function.

This record type is defined in [RFC5155](http://www.rfc-editor.org/rfc/rfc5155.txt).
