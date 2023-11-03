---
Slug: loc-records
Keywords: LOC record type,Location information,GPS
DocID: 43
---
# LOC-Records (Location information)

This record type is used to specify geographical location information about hosts, networks, and subnets.

A LOC-record describes a location with the following properties:

 - Latitude / Longitude.

 - Altitude.

 - Size (diameter of the location described).

 - Horizontal / Vertical precision of the data.

Because of the binary storage format used, only the first digit of the size and precision properties can be non-zero.

Additional interesting and practical information about LOC-records is available at <http://www.ckdhr.com/dns-loc/>

To create a new LOC-record, right-click a zone in the left list in the [DNS Records window](wd_records.md), and select "Other new record" from the pop-up menu.

This record type is defined in [RFC1876](http://www.rfc-editor.org/rfc/rfc1876.txt).
