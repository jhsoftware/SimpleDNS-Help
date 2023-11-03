---
Slug: dnssec-ds-records-dialog
Keywords: DNSSEC,DS
DocID: 65
---
# DNSSEC DS-records dialog

- **DS-record hashing algorithm**\
Specify the algorithm to use for calculating hash.

- **DS-record(s) to be included in parent zone**\

    The DS-record(s) needed to be included (and signed) in the parent zone. For example if your domain name is "example.se", the DS-record needs to be added to the ".se" zone. The procedure for "uploading" the DS-record depends on your parent zone / TLD operator, and/or your domain name registrar.
    For more on this see [DNSSEC](df_dnssec.md).
