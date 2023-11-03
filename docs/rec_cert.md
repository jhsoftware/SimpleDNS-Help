---
Slug: cert-records
Keywords: CERT record type
DocID: 35
---
# CERT-Records (Certificate / CRL)

CERT-records store certificates and related revocation lists (CRL) for cryptographic keys.

CERT-records have the following data elements (see RFC below for details):

- Type: the type of certificate/CRL stored. Select one of the predefined values, or enter a numeric value (0-65535).

- Key tag: A numeric value (0-65535) used the efficiently pick a CERT record.

- Algorithm: the algorithm used .Select one of the predefined values, or enter a numeric value (0-65535).

- Certificate or CRL: Base64 encoded.

To create a new CERT-record, right-click a zone in the left list in the [DNS Records window](wd_records.md), and select "Other new record" from the pop-up menu.

This record type is defined in [RFC4398](http://www.rfc-editor.org/rfc/rfc4398.txt).
