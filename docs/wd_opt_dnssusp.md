---
Slug: options-dialog-dns-local-zones-suspended-zones
Keywords: Suspended Zone
DocID: 87
---
# Options dialog - DNS - Local Zones - Suspended Zones

- **When receiving DNS requests for names or sub-names of suspended zones**\
Select one of the following options to specify how Simple DNS Plus should respond when it receives a DNS request for a name in a [suspended zone](df_suspended.md):

    - **Respond with a "Refused" error message (default)**\
    Using this option, you specifically inform the client (or other DNS server) that you will not provide any data for the requested name.

    - **Respond as if the zone was not configured on this server**\
    The server will respond as if the zone wasn't on this server.\
    If the IP address sending the DNS request is not offered recursion (see [Recursion section](wd_opt_dnsrecur.md)), the request will be treated as lame, and responded to (or not) according to the settings in the [Lame Requests section](wd_opt_dnslamereq.md).

    - **Respond with synthesized DNS records**\
    Using this option, you can redirect anyone requesting suspended names for example to a "this web-site is temporarily suspended" web-page.
