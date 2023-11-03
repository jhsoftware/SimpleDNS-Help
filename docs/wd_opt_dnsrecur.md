---
Slug: options-dialog-dns-resolver-recursion
Keywords: Recursion
DocID: 84
---
# Options dialog - DNS - Resolver - Recursion

- **Perform DNS recursion (resolve non-local domain names)**\
Specify which IP addresses should be offered [recursion](df_recursion.md).\
You can list multiple IP addresses, IP address ranges, and/or IP address subnets.\
For DNS servers accessible from the Internet, it is highly recommend that you limit recursion to IP addresses on the local area network as this prevents DNS cache snooping and helps protect against cache poisoning (spoofing) - see [How to secure your server](ht_secure.md).

- **Maximum recursive DNS requests to resolve in parallel**\
Specifies the maximum number of [recursive](df_recursion.md) requests to resolve at the same time.

- **To protect against cache poisoning (spoofing), only accept responses via UDP which**

    - **Come from the IP address that the corresponding request was sent to**\
    Enabling this option helps protect against DNS spoofing attacks. See [How to secure your server / DNS spoofing](ht_secure.md#spoofing).\
    This is only an option because some multi-homed DNS servers may not respond from the same IP address as the DNS request was sent to, making it is impossible to resolve domains hosted by such a DNS server with this option enabled. This is however pretty rare and we highly recommend enabling this option.

    - **Match randomized letter casing in query name (DNS0X20)**\
    Enabling this option helps protect against DNS spoofing attacks. See [How to secure your server / DNS spoofing](ht_secure.md#spoofing).\
    This is only an option because some older DNS servers/forwarders may respond incorrectly (rare) or not respond at all (very rare) to these requests (randomized letter casing in query name).\
    Simple DNS Plus is able to correct for cases where an incorrect response is provided (query name letter casing mismatch or error code) - this just takes a few extra requests causing a small delay and a bit more network traffic.\
    However, in cases where no response is provided, Simple DNS Plus will not be able to resolve the query. As mentioned, this is very rare, and we highly recommend enabling this option.
