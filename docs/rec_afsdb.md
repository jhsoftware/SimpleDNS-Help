---
Slug: afsdb-records
Keywords: AFSDB record type,Andrew File System
DocID: 32
---
# AFSDB-Records (AFS Data Base location)

An AFSDB-record maps a domain name to an AFS (Andrew File System) database server.

The server name points to an [A-record](rec_a.md) for the database server, and the sub-type indicates server type:\
1 = AFS version 3.0 volume location server for the named AFS cell.\
2 = DCE authenticated server.

To create a new AFSDB-record, right-click a zone in the left list in the [DNS Records window](wd_records.md), and select "Other new record" from the pop-up menu.

This record type is defined in [RFC1183](http://www.rfc-editor.org/rfc/rfc1183.txt).
