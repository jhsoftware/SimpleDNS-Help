---
Slug: dname-records
Keywords: DNAME record type,Non-Terminal,Name Redirection
DocID: 38
---
# DNAME-Records (Non-Terminal DNS Name Redirection)

A DNAME-record is used to map / rename an entire sub-tree of the DNS name space to another domain.

It differs from the [CNAME-record](rec_cname.md) which maps only a single node of the name space.

To create a new DNAME-record, right-click a zone in the left list in the [DNS Records window](wd_records.md), and select "Other new record" from the pop-up menu.

This record type is defined in [RFC2672](http://www.rfc-editor.org/rfc/rfc2672.txt).
