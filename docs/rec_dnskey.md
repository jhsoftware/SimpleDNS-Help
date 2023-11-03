---
Slug: dnskey-records
Keywords: DNSKEY record type
DocID: 39
---
# DNSKEY-Records (DNSSEC public key)

A DNSKEY-record holds a public key that resolvers can use to verify [DNSSEC](df_dnssec.md) signatures in [RRSIG-records](rec_rrsig.md).

DNSKEY-records have the following data elements:

- Flags: "Zone Key" (set for all DNSSEC keys) and "Secure Entry Point" (set for KSK and simple keys).

- Protocol: Fixed value of 3 (for backwards compatibility)

- Algorithm: The public key's cryptographic algorithm.

- Public key: Public key data.

To add a DNSKEY-record to a zone, use the [DNSSEC Sign Zone](wd_signzone.md) function.

This record type is defined in [RFC4034](http://www.rfc-editor.org/rfc/rfc4034.txt).
