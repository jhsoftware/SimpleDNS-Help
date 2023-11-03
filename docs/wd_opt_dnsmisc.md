---
Slug: options-dialog-dns-miscellaneous
Keywords: Miscellaneous,NOTIFY requests,Root server list,Hints file,EDNS0,BIND version requests
DocID: 78
---
# Options dialog - DNS - Miscellaneous

- **Enable Round Robin (rotate DNS records in responses)**\
When this option is enabled and multiple records of the same type are defined for the same name, Simple DNS Plus automatically rotates these records in responses (See [Round Robin](df_rrobin.md)).

- **Synthesize empty reverse zones for standard private IP address ranges**\
This prevents leakage of reverse DNS requests for private IP addresses.\
For details see [draft-ietf-dnsop-default-local-zones](http://tools.ietf.org/html/draft-ietf-dnsop-default-local-zones)

- **Send NOTIFY requests to secondary servers when a primary zone is updated**\
Enables faster synchronization of zone changes to secondary DNS servers.\
Not supported by older DNS server software.

- **Keep the root server list (a.k.a. "hints file") updated automatically**\
With this option enabled, Simple DNS Plus will automatically check for [root server](df_root.md) updates.\
You may want to disable this if you are using an alternate root or if your server is only used on for intranet purposes.

- **Respond to BIND version requests**\
Since many Internet DNS servers are running some version BIND (mainly Unix/Linux DNS server), hackers may initiate an attack by sending a special request for the BIND software version number. They can then compare the response with a list of known vulnerabilities for that particular version of the BIND software and launch the actual attack.\
With this option enabled, Simple DNS Plus will respond to such BIND version requests with a text of your choice.\
When this option is not enabled, Simple DNS Plus will respond to BIND versions requests with a "not implemented" error message.\
A warning is always logged for BIND version requests.

- **Limit client caching time (adjust TTLs in responses to recursive requests)**\
Recent Windows versions have a "DNS Client" service (enabled by default) which caches DNS records locally. Other operating systems have similar features.\
This option can be used to limit the time that client computers/devices cache the DNS records provided by Simple DNS Plus by setting a maximum TTL (time to live) value for DNS records in responses to these clients.\
This is independent of the length of time that Simple DNS Plus might itself cache (see [Options dialog / DNS / Resolver / Caching section](wd_opt_dnscaching.md)) the same DNS records and only takes effect for clients requesting recursion (not other DNS servers) and only for clients with IP addresses in the "Perform recursion for" list (see [Options dialog / DNS / Resolver Recursion section](wd_opt_dnsrecur.md)).\
Limiting client caching time is useful when you want to be able to enforce quick updates - for example when using black/white-lists that are frequently updated, or plug-ins that might take effect at different times.\
NOTE: Microsoft Internet Explorer also caches DNS records (independent of the "DNS Client" service) for 30 minutes no matter what TTL is used. So updates may take up to 30 minutes no matter what unless the user restarts I.E. Other browsers also cache DNS records but typically for a shorter time.

- **EDNS maximum UDP payload size**\
Used in outbound DNS requests (when EDNS is enabled under [DNS / Outbound requests](wd_opt_dnsout.md)) and in outbound responses (when EDNS is present in request) to indicate the maximum UDP payload size that can be received/sent.\
A value of 1280 bytes is a good starting point for most setups, as this payload size fits within the standard Ethernet packet size.
In many cases values of 4096 and higher will also be fine depending on network, routers, etc.

- **UDP requests for \<root\> / UDP 'ANY' requests**\
These option were implemented to deal with specific variations of [DNS reflection/amplification attacks](ht_secure.md#amplification).\
For each type of request (\<root\> / 'ANY') there are 3 options available:\
\- "Normal processing": Requests are handled normally according to other settings etc.\
\- "Ignore (no response)": Requests are simply ignored - no response is sent and no further processing is done.\
\- "Force TCP (empty TC response)": An empty response with the TC (truncated) flag is sent back.\
When using the last option, the response packet is of minimal size and will trigger normal DNS clients/resolvers to resend the request via TCP (basically the TC flag tells the sender that the full response was too big to fit in a UDP packet). The amount of traffic sent to victims is minimized (not amplified) and legitimate requests are still possible.\
Generally, ignoring is more effective and kinder to the attack victims, but may cause some issues.
No standard applications would ever send \<root\> requests, so they should be safe to ignore.
Standard applications should not send 'ANY' requests either, but there are still some old versions of QMail around that rely on this (fixed in later versions).\
For each type of request it is also possible to specify if matching requests should be logged or not.\
Other features are available to deal with DNS reflection/amplification attacks including the [Lame Requests](wd_opt_dnslamereq.md) settings and the Ignore DNS Request [plug-in](pi_overview.md), but this feature filters out these specific packets at an earlier point in the process reducing CPU usage and optionally preventing logging.
