---
Slug: how-to-secure-your-server
Keywords: Security,Spoofing,DNS spoofing,Cache Poisoning,Port scanners,Recursion,DoS (denial of service),Denial of service,BIND version requests,Version requests,DNS rebinding attack,DNS reflection attack,DNS amplification attack
DocID: 25
---
# How to secure your server

As with all types of Internet servers, DNS servers are also targeted by hackers.

The implications can be quite serious, but the good news is that you can protect yourself better by running Simple DNS Plus compared to trusting your ISP's DNS servers.

There are several security issues with DNS, but Simple DNS Plus addresses them all:

## DNS spoofing (a.k.a. "cache poisoning"){#spoofing}

DNS spoofing is the act of injecting false data into the [cache](df_cache.md) of a DNS server causing it to serve this false data to its clients.

This is done by tricking a DNS server into accepting a false DNS response and caching the false DNS records in this.

Hackers may try to do this simply to prevent someone from accessing the Internet (making a DNS server appear to malfunction), but intentions can be more malicious and the effects more serious. For example, by injecting false [MX-records](rec_mx.md), a hacker could re-route e-mails intended for a company's client or vendor to himself. If the hacker also forwards the e-mails to the correct destination, this might go undetected for as long as the hacker cares. Or with an injected [A-record](rec_a.md) (for example, www.bank.com = IP 1.2.3.4) and a cloned web-site for www.bank.com, a hacker could get your pin code, password, credit card number etc. (a good reason to check that such web-sites use a valid SSL certificate).

Simple DNS Plus has several automatic features to prevent DNS spoofing:

1) It only caches DNS responses matching DNS requests that it itself sent (same request ID, query name, and query type) and which it has not yet received a response to.

2) It automatically filters out any DNS records in received DNS responses for which the sending DNS server is not [authoritative](df_authoritative.md).

    This protects against simple DNS spoofing where the false DNS records are included in otherwise normal DNS responses.

3) It uses random request IDs.

    This makes it hard to guess the next request ID and use that for impersonating other DNS servers.

4) It queues duplicate requests (same query name and query type) so that each request is not processed before the previous request has been fully resolved.

    Besides from making the software more efficient, this also prevents so-called [birthday attacks](http://en.wikipedia.org/wiki/Birthday_attack).

    In such an attack, the hacker tries to guess an outbound request ID (for impersonating another DNS server) by sending many identical recursive requests very quickly.

    However with Simple DNS Plus, that strategy won't improve the hackers chances (increase the risk), because when the second and following requests are de-queued and processed, these will be served from the cache and won't cause any outbound requests to resolve.

5) It only accepts incoming responses via UDP which echo and match the request's question section (when/if a response without a question section is received, it switches to TCP).

    This prevents a variant of the so-called [birthday attack](http://en.wikipedia.org/wiki/Birthday_attack) where the hacker sends queries for different sub-names and responds without the question section in order to increase his chances.


Additionally we recommend that you:

1) Use random port numbers for outbound requests (enabled by default). See [Options dialog / DNS / Outbound Requests](wd_opt_dnsout.md) section.

    This makes it harder for hackers to impersonate other DNS servers because they need to correctly guess from which port a request (sent to somewhere else) came from.

2) Limit DNS recursion to your own IP range(s). See [Options dialog / DNS / Resolver / Recursion](wd_opt_dnsrecur.md) section.

    This makes it much harder for anyone on the outside to provoke Simple DNS Plus into doing a recursive DNS lookup at a predictable time (the first step in DNS spoofing).

3) Enable "To protect against cache poisoning (spoofing), only accept responses via UDP which - Come from the IP address that the corresponding request was sent to" in the [Options dialog / DNS / Resolver / Recursion](wd_opt_dnsrecur.md) section (enabled by default).

    This makes it much harder for hackers to impersonate another DNS servers because they also need to spoof that server's IP address.

4) Enable "To protect against cache poisoning (spoofing), only accept responses via UDP which - Match randomized letter casing in query name (DNS0X20)" in the [Options dialog / DNS / Resolver / Recursion](wd_opt_dnsrecur.md) section (enabled by default).

    This makes it harder for hackers to impersonate other DNS servers because they need to correctly guess the letter casing that was used in the query name.

## DNS reflection / amplification attacks{#amplification}

When you send a DNS request to a DNS server, the server will generally send back a response to the IP address that the request network packet appears to come from. So by forging (\*) the sender IP address (IP spoofing) of a DNS request, a hacker can make a DNS server send a response packet to a third party (the victim).

The victim will see the sender IP address as that of the intermediary DNS server, while the hacker remains hidden and very difficult to trace.

This is called a reflection attack.

If the DNS request is constructed in a way that results in a larger response packet (as compared to the request packet), this is called an amplification attack (the hacker achieved a bigger "payload" than if he had sent the packet directly to the victim).

Doing this at a fast rate through many different DNS servers targeting the same IP address, the hacker might overload the victim's DNS server and/or Internet connection (a DDoS attack).

There are many ways to construct DNS requests to achieve amplification (response packet larger than request packet). The following are some of the typical attack requests seen and what can be done to counter them:

 - Requests for \<root\>. 

    By default, many DNS servers will respond to such a request with a list of DNS root servers and associated glue records (typically 26+ records).

    Simple DNS Plus has an option to either ignore these requests or force using TCP - see [Options / DNS / Miscellaneous section](wd_opt_dnsmisc.md).

 - Requests for 'ANY' records for a local domain name.

    Typically such a requests (asking for records of any type) would result in a relatively large DNS response packet listing all the DNS records for the requested name.

    Simple DNS Plus has an option to either ignore these requests or force using TCP - see [Options / DNS / Miscellaneous section](wd_opt_dnsmisc.md).

 - Requests for some domain name that DNS servers are likely to have [cached](df_cache.md) (such as google.com), or for random domain names.

    These are basically "lame requests". So to avoid becoming a participant in such attacks, we recommend configuring Simple DNS Plus to either refuse (default setting) or not respond to lame requests. See [Options / DNS / Lame Requests](wd_opt_dnslamereq.md) section.

    The "Do not respond" option is obviously more efficient against this attack, but may also make it harder to troubleshoot other issues in general (why is the DNS server not responding...).

    With the "Refuse" option, it will still send a response but it won't be amplified (response not larger than request) making your server much less interesting as an intermediary for this attack.

    If you notice an ongoing attack of this type with a specific domain name / record type, you can also block it using the Ignore DNS Request [plug-in](pi_overview.md),

(\*) Forging the sender IP address of a network packet (IP spoofing) is only (practically) possible over the UDP protocol (default protocol for DNS), and is only possible from Internet connections that are not properly protected by the ISP. ISPs should block all outgoing traffic not originating from their own IP address ranges. Most major ISPs do this, but unfortunately not all.

## DNS cache snooping{#snooping}

DNS cache snooping is when someone queries a DNS server in order to find out (snoop) if the DNS server has a specific DNS record cached, and thereby deduce if the DNS server's owner (or its users) have recently visited a specific site.

This may reveal information about the DNS server's owner, such as what vendor, bank, service provider, etc. they use. Especially if this is confirmed (snooped) multiple times over a period.

This method could even be used to gather statistical information - for example at what time does the DNS server's owner typically access his net bank etc. The cached DNS record's remaining TTL value can provide very accurate data for this.

To prevent DNS cache snooping in Simple DNS Plus, simply restrict recursion (see above) to your own IP addresses.

Only IP addresses allowed recursion will get responses with data from the cache.

## DNS rebinding attacks{#rebinding}

This type of attack is not directed at DNS servers directly but rather at web-browsers and other client software.

Simple DNS Plus can however provide a very effective defence against this. 

A web-browser will generally allow any script, Java object, Flash object, etc. to communicate over HTTP / TCP with the server that served the current web-page for as long as that web-page is open in the browser. This is controlled by the host name specified in the web-page URL.

A DNS rebinding attack is done by having the DNS record for the host name time out very quickly (low TTL and other tricks) and then serve a new IP address for the host name in response to the next DNS request ("rebinding").

The new IP address would be the private/local IP address of an intranet server or device at your location. Now with a bit of scripting, the attacker can in effect use your browser as a gateway to your entire intranet - completely bypassing your firewall.

The same type of attack may also be possible with other Internet applications that rely on host names for security.

Browser companies are taking steps to prevent this in new browser versions, but it is much more efficient and secure to stop this type of attack at the DNS level by filtering out any private/local IP addresses in DNS responses from outside DNS servers.

This is configured in the Simple DNS Plus [Options dialog / DNS / Resolver / IP Filtering](wd_opt_dnsrespfilter.md) section.

## DNS recursion / Open DNS server{#recursion}

Internet users (other than your own users) may try to take advantage of your DNS server.

For example, if someone feels that their ISP's DNS server is too slow - they might just use another one - like your's.

This actually happens more frequently than most people would think.

Many ISPs and companies "offer" this service free of charge without even realizing it. This of course consumes additional bandwidth and CPU cycles.

If you do not host any domain names, you could prevent this simply by blocking incoming DNS requests on your firewall, or configure Simple DNS Plus to only listen for DNS requests on a private IP address. See [Options dialog / DNS / Inbound Requests](wd_opt_dnsreq.md) section.

However, if you are hosting one or more domain names (primary or secondary), you must allow other DNS servers access to your DNS servers.

The difference between Internet users and other DNS servers is [recursion](df_recursion.md).

Client applications (users) need the DNS server to perform recursion (fully resolve domain names into IP addresses), whereas other DNS servers perform the recursion themselves.

By specifying only the IP addresses of your own users in the [Options dialog / DNS / Resolver / Recursion](wd_opt_dnsrecur.md) section, you can effectively block outside users, and at the same time allow other DNS servers to requests data for domain names that your are hosting.

If you are not restricting recursion, then you are running an "Open DNS Server" (not a good thing).

Restricting recursion also make your server less vulnerable to DNS spoofing - see above.

## DNS port scanning{#portscanners}

A hacker may use a utility program to search for potential DNS server targets. This software sends dummy DNS requests to a range of IP addresses simply to register which IP addresses return a response. Any IP address that responds will then be probed further for possible vulnerabilities.

Simple DNS Plus has a special "stealth DNS" option which makes it invisible to such scanners, by not responding to a DNS request unless it is for data in local zones or originates from an IP address that is offered recursion.

See [Options dialog / DNS / Lame Requests](wd_opt_dnslamereq.md) section.

## Zone transfers{#zt}

[Zone transfers](df_zonetransfer.md) are intended for use by secondary DNS servers to synchronize with their primary server.

But you can also request a [zone transfer](df_zonetransfer.md) using a number of different tools (including the [Look Up](wd_lookup.md) function in Simple DNS Plus), which will list all the records contained in a [zone](df_zones.md).

This is great for troubleshooting, but you may not want to expose all the data in your [zones](df_zones.md) to strangers.

Hackers could use this to find out what other servers you are running - and with this information launch other types of attacks.

[Zone transfers](df_zonetransfer.md) also require considerably more bandwidth and CPU cycles compared to regular DNS requests.

You can specify which [TSIG keys](df_tsig.md) and/or IP addresses are allowed to request [zone transfers](df_zonetransfer.md) for each [zone](df_zones.md) in the [Zone Properties dialog](wd_zoneprop.md) under the "Zone Transfers" tab, and in the [Options dialog / DNS / Local Zones Zone transfers](wd_opt_dnszt.md) section.

## Denial of service (DoS){#dos}

This is a very simple (yet effective) type of attack - typically done via "drone computers" / "bot networks".

By sending your server(s) an extreme amount of requests which basically use up all your bandwidth and/or processing power, a hacker can effectively prevent valid users and customers from accessing your services.

Simple DNS Plus has an [IP Address Blocking](wd_block.md) function, which can automatically detect such attacks (specifically directed against the DNS server), and ignore subsequent traffic from the hacker's IP address.

The traffic will still use some of your bandwidth, but Simple DNS Plus won't send replies (which would increase the problem) and won't use up the processing power of the machine it is running on.

Another variant of "DoS" is establishing a lot of TCP connections using up all the resources of the target system.

Simple DNS Plus has an option to limit the maximum number of simultaneous inbound TCP connections ([Options dialog / DNS / Inbound Requests](wd_opt_dnsreq.md) section).

The hacker will still be able to use up all these TCP connections and prevent anyone else from making TCP connections to Simple DNS Plus, but at least he won't exhaust system resources and crash Simple DNS Plus and other programs.

DoS attacks are difficult to prevent completely, but if the hacker doesn't succeed in bringing down your systems, he will probably move on to another victim.

## BIND version requests{#bindversion}

Since many Internet DNS servers are running BIND (a Unix/Linux based DNS server), hackers may initiate an attack by sending a special request for the BIND software version number.

They can then compare the response with a list of known vulnerabilities for that particular BIND version and launch the actual attack.

Simple DNS Plus can be configured to respond to these BIND version requests with a text string of your choice (for example: "Sorry - no BIND here!") by enabling the "Respond to BIND version requests" option in the [Options dialog / DNS / Miscellaneous](wd_opt_dnsmisc.md) section.

A warning is always logged ([Active Log View](wd_views.md) and log files) for BIND version requests.

You can test this using the "BIND version" lookup type in the [DNS Look Up tool](wd_lookup.md) included with Simple DNS Plus.

## DNS forwarding{#forwarding}

When you enable [forwarding](df_forward.md), you basically inherit any security issues of the DNS servers that you are forwarding to.

So make sure those DNS servers are also configured securely - or don't forward to them.

Many new users think they need to configure Simple DNS Plus to forward DNS requests to their ISP's DNS servers in order to resolve DNS.

This is a misconception - Simple DNS Plus is perfectly capable of resolving DNS all by itself.

Forwarding to your ISP just adds another step to the process, which makes it take more time resolve, and has the potential of being less secure.

## Dynamic DNS updates / IP spoofing{#dyndns}

If your Simple DNS Plus server is accessible from the Internet, and you enable standard (un-signed) [dynamic updates](df_dyndns.md) for a zone (in the [zone properties](wd_zoneprop.md) dialog) make sure to specify that only local IP addresses are allowed to send update requests, and that your router or firewall filters out any spoofed IP packets coming from the Internet claiming to be from those IP addresses.

Most routers by default filter out any inbound IP packets claiming to be from the standard private IP address ranges (192.168.x.x / 172.16.x.x / 10.x.x.x).

If this is not filtered by the router, a hacker may be able impersonate a trusted local computer by spoofing the origin IP address of the DNS packets, potentially giving him access to change your DNS records.

If you want to receive [dynamic updates](df_dyndns.md) across the Internet, make sure to use [TSIG](df_tsig.md) signed updates only - see [Options dialog / DNS / Local Zones / TSIG Updates section](wd_opt_dnstsig.md).
