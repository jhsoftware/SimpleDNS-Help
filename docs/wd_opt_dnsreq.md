---
Slug: options-dialog-dns-inbound-requests
Keywords: Listen on,Inbound Requests,Round Robin
DocID: 85
---
# Options dialog - DNS - Inbound Requests

- **Listen for DNS requests via / on**

    List of protocol / local IP address / port number sets that Simple DNS Plus listens for inbound DNS requests on.\

    The settings for each entry in the list are:

    - **Protocol**\
    Choose between UDP/TCP (standard DNS), [DoT (DNS over TLS)](df_dotdoh.md), and [DoH (DNS over HTTPS)](df_dotdoh.md).

    - **Local IP address**\
    (Available for UDP/TCP and DoT protocols only)\
    Select the local IP address on which the DNS service will be available.

    - **Port number**\
    Specify the port number on which the DNS service will be available.\
    The default is 53 for UDP/TCP, 853 for DoT, and 443 for DoH.\
    NOTE: Other DNS servers and client computers expect to find your DNS server on the default port numbers above. You should only use a different port number in special situations, for example, if you are mapping port 53 on a NAT router or proxy to a different port number on this computer.

    - **Host name**\
    (Available for DoT and DoH protocols only)\
    Host name used to match up incoming requests.\
    Note: You can have multiple DoT / DoH entries with the same IP address and port number - as long as this host name differs.

    - **SSL/TLS certificate**\
    (Available for the DoT protocol only)\
    Select the SSL/TLS certificate to use - fetched from the Windows certificate store (Local computer / Personal store).\
    DoT requests can use the same SSL/TLS certificate as used by DoH (DNS over HTTPS) and IIS web-sites.

    - **Behind reverse proxy** (get source IP from 'X-Forwarded-For' header)\
    (Available for the DoH protocol only)\
    If this setting is enabled, and an HTTP request has an "X-Forwarder-For" header - that value will be considered to source IP address of the DNS request.\
    Otherwise the source IP address is the network address that the HTTP request originates from.
    Settings related to the source IP address of DNS requests (such as recursion) also apply to incoming DNS requests via DoH.

    - **Use SSL/TLS**\
    (Available for the DoH protocol only)\
    Clients always use SSL/TLS for DoH.\
    The option to serve DoH without SSL/TLS (unchecking this setting) is here in case you want to place a reverse proxy server (with SSL) in front of Simple DNS Plus and provide SSL/TLS encryption that way.

    - **Query URL**\
    (Available for the DoH protocol only)\
    The full URL that Simple DNS Plus will listen for DoH requests on.\
    Note that the path / page is fixed as "/doh/dns-query" and cannot be changed.

    For the DoH protocol, there is also a **Bind SSL certificate** button available.\
    The easiest way to setup SSL for DoH is if you are also running an SSL based web-site on IIS on the same computer as Simple DNS Plus, and you configure DoH to be served under the same host name as that site. This way you can just manage the SSL certificate in IIS.\
    However, if you are NOT doing this or if you want to use a different SSL/TLS certificate for DoH (DNS over HTTPS), you will need to "bind" an SSL/TLS certificate to the host name (and port) used. This button will do that.


- **Maximum inbound DNS TCP connections per source IP address**\
    A hacker may try to open a lot of TCP connections to exhaust server resources.\
    Use this option to limit the number of simultaneous inbound TCP connections Simple DNS Plus will accept from one IP address. When this number of connections has been reached additional connection attempts from the IP address are logged and then rejected.
