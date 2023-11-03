---
Slug: cname-records
Keywords: CNAME record type,Canonical name,Alias
DocID: 36
---
# CNAME-Records (Canonical name for an alias)

CNAME-records are domain name aliases.

Computers on the Internet often performs multiple roles such as web-server, ftp-server, chat-server etc.

To mask this, CNAME-records can be used to give a single computer multiple names (aliases).

For example, the computer "computer1.xyz.com" may be both a web-server and an ftp-server, so two CNAME-records are defined:

"www.xyz.com" = "computer1.xyz.com" and "ftp.xyz.com" = "computer1.xyz.com".

Sometimes a single server computer hosts many different domain names (take ISPs), and so CNAME-records may be defined such as "www.abc.com" = "www.xyz.com".

The most common use of the CNAME-record type is to provide access to a web-server using both the standard "www.domain.com" and "domain.com" (with and without the www prefix).

This is usually done by creating an [A-record](rec_a.md) for the short name (without www), and a CNAME-record for the www name pointing to the short name.

CNAME-records can also be used when a computer or service needs to be renamed, to temporarily allow access through both the old and new name.

A CNAME-record should always point to an [A-record](rec_a.md) and never to itself or another CNAME-record to avoid circular references.

To create a new CNAME-record, right-click a zone in the left list in the [DNS Records window](wd_records.md), and select "New CNAME-record" from the pop-up menu.

Please note that you cannot create a CNAME-record for the zone name itself as this will always conflict with the zone's [SOA-record](rec_soa.md). For more on this see <https://simpledns.plus/kb/158>

This record type is defined in [RFC1035](http://www.rfc-editor.org/rfc/rfc1035.txt).
