---
Slug: dns-look-up-window-look-up-types
Keywords: Look Up Types
DocID: 71
---
# DNS Look Up Window - Look Up Types

## Forward DNS lookup

To do a forward (normal) DNS lookup, first enter the domain name that you want to look up, and then select one of the record types in the first section of the lookup menu or in the "Other record type" sub-menu.

## Reverse DNS lookup

To do a [reverse](df_reverse.md) lookup (IP address to domain name), simply enter the IP address as the domain name, and do a [PTR-record](rec_ptr.md) look up. The IP address will automatically be converted to a [reverse DNS](df_reverse.md) domain name.

## "Any DNS record" lookup

This type of lookup will return DNS records of any type for the requested domain name.

This is NOT necessarily the same as "all" records for the domain name.

If the DNS server that you sent the request to happens to have some records cached for the domain name, it will simply return those.

The records that the DNS server has cached may be the result of a previous lookup for a specific record type and/or different record type for the domain name may have different [TTL](df_ttl.md) values, and therefore the DNS server cache may not contain all available records type for a domain name.

The only way to ensure that an "any DNS record" lookup returns all the records for a domain name is to query one of the [authoritative](df_authoritative.md) DNS servers for the domain directly.

NOTE: Some DNS servers are configured to refuse DNS requests for "ANY" record type.

## Zone Transfer lookup

This will list all the records in a zone.

[Zone transfers](df_zonetransfer.md) are typically used by secondary DNS servers to synchronize a DNS [zone](df_zones.md) with the primary DNS server.

NOTE: Most DNS servers are (and should be) configured to only allow [TSIG](df_tsig.md) signed zone transfers (not possible in Look Up Window) and/or zone transfer requests from specific IP addresses - typically secondary DNS servers.

## BIND Version lookup

This can be used to send a special DNS request asking for the software version of a BIND DNS server (a Unix/Linux DNS server).

Default BIND DNS server configurations will return will return the version number of the BIND software.

However for security reasons, many DNS servers (BIND and others) are configured not to respond to such requests, or to respond with some message indicating that they won't tell you their version number.

Simple DNS Plus can also be configured to respond to BIND version requests - see [Options dialog / DNS / Miscellaneous](wd_opt_dnsmisc.md) section.

## WHOIS lookup

The WHOIS look up function provides detailed information (such as name, address and phone) about the owners of a domain name or IP address.

This is done through special WHOIS servers maintained by the organizations responsible for the top level domains ("TLDs") around the world.

Simple DNS Plus comes with a recent list of these servers and will automatically select the best match when the "Auto WHOIS Server" option in the Tool menu is selected (default).

You can add new WHOIS servers to the list by manually editing the "whois.dat" file found in the Simple DNS Plus directory.

If you do a WHOIS lookup for a top level domain not listed in the "whois.dat" file, the lookup tool will try to use the server name "whois.nic." + the last segment of the domain name entered, as this is the most common WHOIS server name.
