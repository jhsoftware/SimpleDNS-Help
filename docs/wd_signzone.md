---
Slug: dnssec-sign-zone-dialog
Keywords: DNSSEC,Sign zone
DocID: 104
---
# DNSSEC Sign Zone dialog

For more information on how these settings work, see [DNSSEC](df_dnssec.md).

- **Use on-line DNSSEC keys.**\
Check this to use on-line DNSSEC keys for signing.

    - **Edit...**\
    Click this button to edit the on-line keys for the selected zone - using the [DNSSEC Keys dialog](wd_dnsseckeys.md).

- **Use off-line DNSSEC keys from a file**\
 Check this to use keys from a DNSSEC key file (containing off-line keys) when signing the zone.\
    Specify the full path to the DNSSEC key file.

    - **Browse**\
    Click this button to browse the local file system for a key file.

    - **Create new...**\
    Click this button to create a new key file - using the [DNSSEC Keys dialog](wd_dnsseckeys.md).

    - **Edit...**\
    Click this button to edit an existing key file - using the [DNSSEC Keys dialog](wd_dnsseckeys.md).

- **KSK / Simple key signatures expire after**\
When signatures made with KSKs / Simple keys should expire.\
Keep in mind that the zone needs to be re-signed before this happens - also allowing for record TTLs.

- **ZSK signatures expire after**\
When signatures made with ZSKs should expire.
Keep in mind that the zone needs to be re-signed before this happens - also allowing for record TTLs.

- **"Sign zone" button**\
[DNSSEC](df_dnssec.md) sign the zone.
    
    If the keys used (on-line + off-line) include a KSK or a Simple key, then ALL DNSSEC records (including DNSKEY records) will be wiped and then re-created.\
    If the keys are only ZSKs, then existing DNSKEY records and RRSIG records signing the DNSKEY records will be left alone.
