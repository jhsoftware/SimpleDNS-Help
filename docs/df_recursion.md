---
Slug: definition-recursion
Keywords: Recursion,Recursive,Non-recursive,Resolution,DNS Recursion,DNS Resolution
DocID: 9
---
# Definition - Recursion

DNS requests can either be "recursive" or "non-recursive".

Client applications (such as Internet browsers) request that the DNS server performs recursion for them by setting an RD (Recursion Desired) flag in the request packet. This is a recursive request.

Client applications do this both because they do not posses the ability to resolve domain names themselves, and also to take advantage of centralized [caching](df_cache.md) on the DNS server.

However, when a DNS server sends requests to other DNS servers as part of the recursion process, these requests are typically non-recursive (the RD flag is not set).

The DNS server indicates back to the client if it is willing to perform recursion by setting or not setting an RA (Recursion Available) flag in the DNS response packet.

When a DNS server receives a recursive request from a client that it is willing to perform recursion for, it will go through the process of resolving the requested domain name by first asking the [root servers](df_root.md), which respond with a referral to the top level DNS servers, then asking one of those servers, which respond with a referral to the next level DNS servers, etc.

When a DNS server receives a non-recursive request or a request from a client that it is not willing to perform recursion for, it typically responds immediately with whatever local data it has available at the time without doing any additional processing.

Simple DNS Plus can also be configured to respond to such requests with an error, with synthesize records, or not respond at all. This is configured in the [Options dialog / DNS / Lame Requests section](wd_opt_dnslamereq.md).

A recursive DNS request requires much more processing by the server compared to a non-recursive request.

So it is important to configure Simple DNS Plus to only offer recursion to trusted clients.

You can configure this in the [Options dialog / DNS / Resolver / Recursion](wd_opt_dnsrecur.md) section.

NOTE: For programs like browsers and e-mail clients to work, they must have access to a DNS server that offers recursion. Therefore local computers (including the server itself) should always be offered recursion.
