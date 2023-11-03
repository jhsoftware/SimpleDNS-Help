---
Slug: hinfo-records
Keywords: HINFO record type,Host information
DocID: 41
---
# HINFO-Records (Host information)

A HINFO-record specifies the host / server's type of CPU and operating system.

This information can be used by application protocols such as FTP, which use special procedures when communicating with computers of a known CPU and operating system type.

Standard CPU and operating system types are defined in [RFC1700](http://www.rfc-editor.org/rfc/rfc1700.txt) (Page 206 / 214).

The standard for a Windows PC is "INTEL-386" / "WIN32".

To create a new HINFO-record, right-click a zone in the left list in the [DNS Records window](wd_records.md), and select "Other new record" from the pop-up menu.

This record type is defined in [RFC1035](http://www.rfc-editor.org/rfc/rfc1035.txt).
