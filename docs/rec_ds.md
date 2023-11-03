---
Slug: ds-records
Keywords: DS record type
DocID: 40
---
# DS-Records (Delegation Signer)

DS-records are used to secure delegations ([DNSSEC)](df_dnssec.md).

A DS-record with the name of the sub-delegated [zone](df_zones.md) is placed in the parent zone along with the delegating [NS-records](rec_ns.md).

This DS-record references a [DNSKEY-record](rec_dnskey.md) in the sub-delegated zone.

DS-records have the following data elements:

- Key Tag: A short numeric value which can help quickly identify the referenced [DNSKEY-record](rec_dnskey.md).

- Algorithm: The algorithm of the referenced DNSKEY-record.

- Digest Type: Cryptographic hash algorithm used to create the Digest value.

- Digest: A cryptographic hash value of the referenced DNSKEY-record.

To create a new DS-record, right-click a zone in the left list of [DNS Records window](wd_records.md), and select "Other new record" from the pop-up menu.

This record type is defined in [RFC4034](http://www.rfc-editor.org/rfc/rfc4034.txt).
