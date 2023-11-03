---
Slug: options-dialog-dns-lame-requests
Keywords: Lame DNS Requests,Stealth DNS
DocID: 77
---
# Options dialog - DNS - Lame Requests

- **When receiving lame DNS requests**\
Select one of the following options to specify how/if Simple DNS Plus should respond to lame DNS requests:

    - **Respond with a "Refused" error message (default)**\
    Using this option, you inform the server/client sending the request that you will not perform any recursion for them or provide any data for the requested domain name.

    - **Do not respond (stealth DNS)**\
    Using this option, simple port scanning will not reveal that you are running a DNS server. This may make you a less interesting target for hackers.

    - **Respond with a referral to Internet root DNS servers**\
    This option is available only because some DNS test tools, including some used by major domain name registrars, expect to see a root referral in response to requests for dummy/random domain names.\
    Unless needed for such tests, we do we do not recommend using this option because it might be abused for [DNS amplification attacks](ht_secure.md#amplification).

    - **Respond with synthesized DNS records**\
    Using this option, you can redirect the client to a sign up page, or to a page informing the client that he is using a wrong DNS server.


> [!BLUE] **What is a "lame DNS request?**
>
> A lame DNS request, is a DNS request sent to a DNS server which is not configured with the requested domain name (local [zones](df_zones.md) or otherwise), and where either:\
> a) recursion is not requested (RD flag not set in request), or\
> b) the receiving DNS server is not configured to perform [recursion](df_recursion.md) for client (typically based on the IP address of the client IP).
