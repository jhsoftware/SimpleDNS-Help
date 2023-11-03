---
Slug: rrsig-records
Keywords: RRSIG record type
DocID: 52
---
# RRSIG-Records (RRset Signature)

An RRSIG-record holds a [DNSSEC](df_dnssec.md) signature for a record set (one or more DNS records with the same name and type).

Resolvers can verify the signature with a public key stored in a [DNSKEY-record](rec_dnskey.md).

RRSIG-records have the following data elements:

- Type Covered: DNS record type that this signature covers.

- Algorithm: Cryptographic algorithm used to create the signature.

- Labels: Number of labels in the original RRSIG-record name (used to validate wildcards).

- Original TTL: [TTL](df_ttl.md) value of the covered record set.

- Signature Expiration: When the signature expires.

- Signature Inception: When the signature was created.

- Key Tag: A short numeric value which can help quickly identify the [DNSKEY-record](rec_dnskey.md) which can be used to validate this signature.

- Signer's Name: Name of the [DNSKEY-record](rec_dnskey.md) which can be used to validate this signature.

- Signature: Cryptographic signature.

To add RRSIG-records to a zone, use the [DNSSEC Sign Zone](wd_signzone.md) function.

This record type is defined in [RFC4034](http://www.rfc-editor.org/rfc/rfc4034.txt).
