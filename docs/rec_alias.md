---
Slug: alias-records
Keywords: ALIAS record type
DocID: 33
---
# ALIAS-Records (Auto Resolved Alias)

ALIAS-records are virtual alias records resolved by Simple DNS Plus at at the time of each request - providing "flattened" (no CNAME-record chain) synthesized records with data from a hidden source name.

This can be used for different purposes - including solving the classic problem with CNAME-records at the domain apex (for the zone name / for "the naked domain").

To create a new ALIAS-record, right-click a zone in the left list of [DNS Records window](wd_records.md), and select "New ALIAS-record" from the pop-up menu.

For more details on this record type see <https://simpledns.plus/kb/2>
