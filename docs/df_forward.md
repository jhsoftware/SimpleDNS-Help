---
Slug: definition-forwarding
Keywords: Forwarding,DNS forwarding,Extended forwarding,Shadow forwarding,Conditional forwarding
DocID: 6
---
# Definition - Forwarding

When Simple DNS Plus receives DNS request for a domain name configured for forwarding ([Options dialog / DNS / Forwarding section](wd_opt_dnsforward.md)), it skips the normal DNS [resolution](df_recursion.md) process and instead forwards the DNS request to the specified DNS servers asking them to do the resolution work for it.

If local data (own zones / cached records) matching the DNS request already exist, the request will not be forwarded, but rather replied to immediately using this local data.

This also means that setting up DNS forwarding for a domain name which is also a local zone has no effect - data will always be served from the local zone and requests are never forwarded (with the exception of "shadow forwarding" - see below).

You can configure Simple DNS Plus to use forwarding for all domain names and/or for specific domains (including their sub-names), and to use extended and shadow forwarding:

## Forwarding for all domain names

You can use forwarding for all domain names, for example, if you have multiple local DNS servers and wish to build up a central [cache](df_cache.md) on one or a few DNS servers, thereby limiting the DNS traffic sent over your Internet connection.

In this case you would setup one (or a few) DNS servers (the central servers) to do normal resolution with no forwarding, and setup the remaining DNS servers to forward requests for all domains to these central servers.

IMPORTANT: We have noticed that for no apparent reason many users have configured Simple DNS Plus (and other DNS servers) to forward DNS requests for all domain names to their ISP's DNS servers.

Generally we do NOT recommend doing this.

Simple DNS Plus is fully capable of resolving any Internet domain name without the help of any forward DNS servers.

Very often forwarding to your ISP's DNS servers only make resolution slower, as this adds another lookup step to the resolution process, and often ISP DNS servers are overloaded and slow to respond.

By forwarding DNS requests to your ISP's DNS servers, you also inherit any [security issues](ht_secure.md) that those DNS servers might have.

For example, if your ISP's DNS servers are spoofed - so is your DNS server.

However in certain situations, for example, if your Internet connection is slow, it may be appropriate to forward DNS requests to your ISP in order to limit traffic on your own connection and take advantage of DNS [caching](df_cache.md) on your ISP's DNS servers.

## Domain specific forwarding (a.k.a. "conditional forwarding")

You can use domain specific forwarding, for example, if you wish to be able to resolve both Internet domain names as well as a private domain name hosted on another DNS server.

In this case you would configure forwarding specifically for the private domain name only.

## Extended Forwarding

Standard forwarding only forwards [recursive](df_recursion.md) DNS requests, and only when the request originates from an IP address which is offered recursion ([Options dialog / DNS / Recursion section](wd_opt_dnsrecur.md)).

However Simple DNS Plus also has a unique "extended forwarding" option which, when enabled, causes ALL DNS requests for the specified domain and sub-names to be forwarded.

There are several scenarios in which you might want to do this, for example:

 - You are hosting part of your DNS data on a separate DNS server, but you only have one public IP address available for hosting DNS.

 - You are hosting some or all of your DNS data on a separate specialized DNS server (for example; an RBL list server) which requires a lot of resources (for example; serving data from a database), and you want to offload this by having Simple DNS Plus sit in front of it caching the data, and thereby causing fewer requests to hit the specialized DNS server.

 - You are hosting some or all of your DNS data on a separate DNS server which you don't want to expose directly to the Internet (for example; if you have to use some other DNS software with known vulnerabilities). Simple DNS Plus will only forward standard DNS requests, only for the specified domain name, and it automatically filters out most malformed data.

In all 3 scenarios, you can setup Simple DNS Plus on a computer with both a private IP address and a public IP address (or with a public IP address NAT mapped to it), setup the other DNS server on an private IP address only, and configure Simple DNS Plus to use extended forwarding for domains hosted on the other DNS server.

## Shadow Forwarding

Standard DNS forwarding only forwards request which are not for the name or sub-name of a local DNS zone.

However Simple DNS Plus also has a unique "shadow forwarding" option which, when enabled, causes DNS requests for the name or sub-name of a local DNS zone to also be forwarded when no matching DNS records exist in that zone.
