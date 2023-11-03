---
Slug: tlsa-records
Keywords: TLSA record type
DocID: 55
---
# TLSA-Records (Transport Layer Security Authentication)

TLSA records are used to specify the keys used in a domain's TLS servers.

The TLSA record identification (record name) is made of of 3 parts:

- Port number: The port number that the TLS server listens on.

- Protocol: The protocol used (udp, tcp, sctp, or user defined).

- Server host name: Host name of the TLS server.

TLSA-records have the following data elements (see RFC below for details):

- Certificate usage: A numeric value (0-255).

- Selector: A numeric value (0-255).

- Matching type: A numeric value (0-255).

- Certificate association data: Hexadecimal.

To create a new TLSA-record, right-click a zone in the left list in the [DNS Records window](wd_records.md), and select "Other new record" from the pop-up menu.

This record type is defined in [RFC6698](http://www.rfc-editor.org/rfc/rfc6698.txt).
