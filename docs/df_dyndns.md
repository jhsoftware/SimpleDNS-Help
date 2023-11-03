---
Slug: definition-dynamic-dns-update
Keywords: Dynamic DNS update,TSIG
DocID: 5
---
# Definition - Dynamic DNS update

Dynamic DNS updates are used to create and update DNS records directly via the DNS protocol.

Simple DNS Plus supports standard (un-signed) dynamic updates ([RFC2136](http://www.rfc-editor.org/rfc/rfc2136.txt)) and [TSIG](df_tsig.md) signed dynamic updates ([RFC2845](http://www.rfc-editor.org/rfc/rfc2845.txt)).

Standard dynamic updates are configured for each primary zone in the [zone properties dialog](wd_zoneprop.md).

TSIG signed dynamic updates are configured by setting up keys in the [Options dialog / DNS / Local Zones / TSIG Updates section](wd_opt_dnstsig.md).

Standard dynamic updates can be secured by specifying which IP addresses are allowed to send such updates.

This is simple and efficient in a secure environment such as an intranet.

For updates sent over the Internet where the originating IP address may not be known beforehand (dynamic IP) and does not guarantee the identity of the sender (IP spoofing), the dynamic DNS update can be authenticated using a transaction signature (TSIG).

This is a method of cryptographically signing the update data with a key name / value pair (similar to a user name / password pair).

The key name identifies the client to the DNS server, and the key value is a shared secret known only by this client and the DNS server.

Client applications supporting dynamic DNS updates:

 - Recent versions of Microsoft Windows (Me, 2000, and later) have a TCP/IP option "Register this connection's addresses in DNS" which uses dynamic DNS update to automatically update DNS records for itself.\
    Standard dynamic updates are used by default. TSIG authenticated updates are not supported.

 - Several Internet dynamic IP address update clients support TSIG authenticated dynamic DNS updates.\
    For example: "DynSite" from <http://noeld.com/dynsite.asp> or "DirectUpdate" from <http://www.directupdate.net>

**See also**:

The DynDNS Service [plug-in](pi_overview.md) (see <https://simpledns.plus/plugin-dyndns>) also supports TSIG signed dynamic updates over DNS as well as several HTTP based update methods and is specifically targeted towards "DynDNS" scenarios (computers with dynamic IP addresses on the Internet).
