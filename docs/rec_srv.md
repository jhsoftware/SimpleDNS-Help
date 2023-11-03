---
Slug: srv-records
Keywords: SRV record type,location of service,LDAP,Directory services
DocID: 54
---
# SRV-Records (location of service)

SRV-records are used to specify the location of a service.

They are used in connection with different directory servers such as LDAP (Lightweight Directory Access Protocol), and Windows Active Directory, and more recently with SIP servers (see <https://simpledns.plus/kb/112>).

The SRV record identification (record name) is made of of 3 parts:

- Service: Most internet services are defined in [RFC1700](http://www.rfc-editor.org/rfc/rfc1700.txt) (page 15).

- Protocol: Generally TCP or UDP, but other values are also valid.

- Domain name.

The "service location" is specified through a priority, weight, port and target:

 - Priority is a preference number used when more servers are providing the same service (lower numbers are tried first).

 - Weight is used for advanced load balancing.

 - Port is the TCP/UDP port number on the server that provides this service.

 - Target is the domain name of the server (referencing an [A-record](rec_a.md) or [AAAA-record](rec_aaaa.md)).

To create a new SRV-record, right-click a zone in the left list in the [DNS Records window](wd_records.md), and select "Other new record" from the pop-up menu.

This record type is defined in [RFC2782](http://www.rfc-editor.org/rfc/rfc2782.txt).

Note: While this record type could potentially have been used by web-browser software (to locate web-servers), this was never implemented by any major browsers. Instead browsers have recently (2021) started supporting the [HTTPS record-type](rec_https.md) which provdides similar functionality specifically for web-sites.
