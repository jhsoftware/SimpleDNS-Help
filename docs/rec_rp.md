---
Slug: rp-records
Keywords: RP record type,Responsible person
DocID: 51
---
# RP-Records (Responsible person)

An RP-record specifies the mailbox of the person responsible for a host (domain name).

A [SOA-record](rec_soa.md) defines the responsible person for an entire [zone](df_zones.md), but a zone may contain many individual hosts / domain names for which different people are responsible.

The RP-record type makes it possible to identify the responsible person for individual host names contained within the zone.

Optionally specify the domain name for a [TXT-record](rec_txt.md) with additional information (such as phone and address).

To create a new RP-record, right-click a zone in the left list in the [DNS Records window](wd_records.md), and select "Other new record" from the pop-up menu.

This record type is defined in [RFC1183](http://www.rfc-editor.org/rfc/rfc1183.txt).
