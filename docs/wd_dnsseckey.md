---
Slug: new-dnssec-key-dialog
Keywords: DNSSEC,key
Notes: was wd_keyset prior to v. 8
DocID: 63
---
# New DNSSEC Key dialog

This dialog is used to create a new [DNSSEC](df_dnssec.md) key.

- **Key ID**\
    A unique identifier for this key.\
    Only used to identify each key set for management purposes. Not part of actual keys/signatures.\
    Can be any value you want.

- **Key type**\
    For details on the 3 key types, see [DNSSEC definition](df_dnssec.md)

- **Algorithm**\
    Specify the algorithm to use for calculating signatures.

- **Key size (bits)**\
    Specify the key strength.

- **Tag**\
An integer value calculated from the corresponding DNSKEY record data (public key and other settings).\
This is used to quickly identify signature records (RRSIG) which were generated using this key.

- **Created**\
The date/time when this key was created.


- **DNSKEY only / Do not sign any record sets (key pre-publish / phase-out)**\
    Check this if you don't want any record sets signed by this key (but still want to include the DNSKEY record).\
    This is typically used in "key pre-publish" or "key phase-out" scenarios.

- **Delete**\
Schedule the key for deletion.

    The key will be deleted automatically only if:
    1. This is an on-line key.
    2. The remaining on-line keys for the zone include at least one KSK/Simple key not marked "DNSKEY only" (needed to re-sign the updated DNSKEY records after deleting this key).
    3. The key is marked "DNSKEY only" - or - at least one other key of the same type remains after deleting.

    Note this setting can be set automatically for ZSKs when zone is configured to automatically generate/remove ZSKs at an interval in the DNSSEC tab in the [Zone Properties dialog](wd_zoneprop.md)).

- **Notes (internal use only)**\
Use to store any comments about the key.
