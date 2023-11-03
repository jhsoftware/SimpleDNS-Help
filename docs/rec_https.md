---
Slug: https-records
Keywords: HTTPS record type,HTTPS Service binding and parameter specification
DocID: 42
---
# HTTPS-Records (HTTPS Service binding and parameter specification)

HTTPS-records allows browsers to efficiently obtain complete instructions for accessing a web-site for a domain name - including supported protocols (HTTP/1.1, 2, 3, etc.), ip address(es), port number, and public keys (all optional) - saving the browser from doing a number of DNS lookups and other protocol negotiation steps.

An HTTPS-record provides instructions for accessing a web-site with the following properties:

- **Mode**   
    Choose between: Service, Alias, or Service not available / does not exist.\
    In "Alias" mode, the HTTPS-record functions similar to a [CNAME-record](rec_cname.md) - execept only for HTTPS-record requests - which means that it can also appear a the zone name level (unlike CNAME).

- **Priority**\
    The  order of priority (1-65535) - if multiple HTTPS records are available for the same name.

- **Service host name**\
    The host name of the web-server.

- **Protocol identifiers (ALPN IDs)**\
    The ALPN (Application Layer Protocol Negotiation)  IDs of the protocols supported by the web-server.\
    The default is "http/1.1" - meaning HTTP version 1.1.\
    See the official list of ALPN IDs at <https://www.iana.org/assignments/tls-extensiontype-values/tls-extensiontype-values.xhtml#alpn-protocol-ids>\
    For example, "h2" means HTTP v. 2 and "h3" means HTTP v. 3.
    Identifiers in the format "h3-[draft]" like "h3-27" have also been observed "in the wild".

- **IP address(es)** (optional)\
    The IP addresses (IPv4 and/or IPv6) of the server(s) hosting the web-site.\
    This is considered a hint only - a client may choose to resolve the host name property instead of using this.

- **Port number** (optional)\
    An alternate port number for the web-server (other than 443).

- **Encrypted ClientHello (ECH)** (optional)\
    ECH configuration (ECHConfigList) for the web-server encoded in Base64 format. 





To create a new HTTPS-record, right-click a zone in the left list in the [DNS Records window](wd_records.md), and select "Other new record" from the pop-up menu.

This record type is defined in <https://datatracker.ietf.org/doc/draft-ietf-dnsop-svcb-https>
(Not yet an official RFC at the time of this writing, but expected to be so soon)
