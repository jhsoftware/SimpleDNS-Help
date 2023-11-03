---
Slug: definition-reverse-dns
Keywords: Reverse Look Up,Reverse Zone,in-addr.arpa,ip6.arpa,arpa,PTR
DocID: 10
---
# Definition - Reverse DNS

Reverse DNS is IP address to domain name mapping - the opposite of forward (normal) DNS which maps domain names to IP addresses.

Reverse DNS is maintained in a separate set of data from forward DNS.

For example, forward DNS for "abc.com" pointing to IP address "1.2.3.4", does not necessarily mean that reverse DNS for IP "1.2.3.4" points to "abc.com".

Reverse DNS is mostly used by humans for such things as tracking where a web-site visitor came from, or where an e-mail message originated, etc.

Reverse DNS is typically not as critical in as forward DNS - visitors will still reach your web-site just fine without any reverse DNS for your web-server IP or the visitor's IP.

However there is one important exception: Many e-mail servers on the Internet (including AOL's) are configured to reject incoming e-mails from any IP address which does not have reverse DNS.

So if you run your own e-mail server, reverse DNS must exist for the IP address that outgoing e-mail is sent from.

In most cases it does not matter what the reverse DNS record for your IP address points to as long as it is there. If you host multiple domains on one e-mail server, just setup a single reverse DNS record to point to whichever domain name you consider primary.

(e-mail servers checking for reverse DNS know that it is normal to host many domains on a single IP address and it would be impossible to list all those domains in reverse DNS for the IP).

A special [PTR-record](rec_ptr.md) type is used to store reverse DNS entries.

In Simple DNS Plus, a [zone](df_zones.md) for reverse DNS records is created using the [New Zone](wd_newzone.md) function in the [DNS Records window](wd_records.md).

Reverse records can also be created automatically by checking "Update reverse zone" in the [Record Properties](wd_recprop.md) dialog when editing [A-Records](rec_a.md) or [AAAA-records](rec_aaaa.md).

Reverse DNS is also different from forward DNS in who points (delegates) the zone to your DNS server.

With forward DNS, you delegate the zone to your DNS server by registering that domain name with a registrar.

With reverse DNS, your Internet connection provider (ISP) must delegate the reverse zone to your DNS server.

Without this delegation from your ISP, your reverse zone will not work.

## IPv4 specifics

For IPv4, the name of a reverse DNS PTR-record is the IP address with the segments reversed + ".in-addr.arpa".

For example, the reverse DNS entry for IP "1.2.3.4" would be stored as a PTR-record for "4.3.2.1.in-addr.arpa".

If you are assigned the class C network 1.2.3.X, your ISP can delegate DNS authority for the "3.2.1.in-addr.arpa" domain name to your DNS server.

Your DNS servers should in this case have a [zone](df_zones.md) called "3.2.1.in-addr.arpa" containing [PTR-records](rec_ptr.md) for all active IP addresses in the class C network (1.2.3.0 - 1.2.3.255).

Simple DNS Plus provides an easy to use [Reverse zone name-to-IP mappings dialog](wd_iptoname.md) which makes it easy to maintain reverse IPv4 zones and records (without dealing with "in-addr.arpa", reversing IP addresses etc.). This is accessible from the bottom of the [DNS Records window](wd_records.md) whenever an IPv4 reverse zone is selected.

It is also possible to delegate "in-addr.arpa" authority for less than one class C network (256 IP addresses).

This can be achieved in different ways, but typically follows the style described in [RFC2317](http://www.rfc-editor.org/rfc/rfc2317.txt).

(Please note: Many ISPs will not do this sub-delegation if you only have one or a few IP addresses. In this case your ISP has probably already setup some default reverse DNS for your IP addresses)

For example, if you are assigned network 1.2.3.24/29 (1.2.3.25 to 1.2.3.30 subnet mask 255.255.255.248), the owner of the class C 1.2.3.X (your ISP) would have these DNS entries on his DNS server:

```
NS  24/29.3.2.1.in-addr.arpa = your-dns-server-name1
NS  24/29.3.2.1.in-addr.arpa = your-dns-server-name2
CNAME  25.3.2.1.in-addr.arpa = 25.24/29.3.2.1.in-addr.arpa
CNAME  26.3.2.1.in-addr.arpa = 26.24/29.3.2.1.in-addr.arpa
CNAME  27.3.2.1.in-addr.arpa = 27.24/29.3.2.1.in-addr.arpa
CNAME  28.3.2.1.in-addr.arpa = 28.24/29.3.2.1.in-addr.arpa
CNAME  29.3.2.1.in-addr.arpa = 29.24/29.3.2.1.in-addr.arpa
CNAME  30.3.2.1.in-addr.arpa = 30.24/29.3.2.1.in-addr.arpa
```

And your DNS server would have a [zone](df_zones.md) named "24/29.3.2.1.in-addr.arpa" with the following records:

```
NS  24/29.3.2.1.in-addr.arpa = your-dns-server-name1
NS  24/29.3.2.1.in-addr.arpa = your-dns-server-name2
PTR  25.24/29.3.2.1.in-addr.arpa = name1.your-domain-name
PTR  26.24/29.3.2.1.in-addr.arpa = name2.your-domain-name
PTR  27.24/29.3.2.1.in-addr.arpa = name3.your-domain-name
PTR  28.24/29.3.2.1.in-addr.arpa = name4.your-domain-name
PTR  29.24/29.3.2.1.in-addr.arpa = name5.your-domain-name
PTR  30.24/29.3.2.1.in-addr.arpa = name6.your-domain-name
```

A reverse lookup for IP 1.2.3.27 ([PTR-record](rec_ptr.md) for "27.3.2.1.in-addr.arpa"), would first return an alias ([CNAME-record](rec_cname.md)) for "27.24/29.3.2.1.in-addr.arpa" from the class C owner's DNS server, which is then translated to "name3.your-domain-name" by your DNS server.

## IPv6 specifics

For IPv6, the name of a reverse DNS PTR-record is each hex digit of the IP address in reverse order, with dots between each digit, and with "ip6.arpa" appended to the end.

For example, the reverse DNS entry for IP "1234:5678:90ab:cdef:1234:5678:90ab:cdef" would be stored as a PTR-record for "f.e.d.c.b.a.0.9.8.7.6.5.4.3.2.1.f.e.d.c.b.a.0.9.8.7.6.5.4.3.2.1.ip6.arpa".

IPv6 reverse zones can be delegated at the hex digit level. So the smallest possible delegation would be for 16 IPv6 addresses, then 256, then 4096, etc.
