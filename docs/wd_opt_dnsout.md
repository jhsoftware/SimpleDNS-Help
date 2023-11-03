---
Slug: options-dialog-dns-outbound-requests
Keywords: Outbound Requests,From port number
DocID: 83
---
# Options dialog - DNS - Outbound Requests

- **Send DNS and zone transfer requests via**\
    Specify which IP versions (IPv4/IPv6) and from which local IP addresses outbound requests should be sent.\
    It can be useful to select a specific local IP address for secondary DNS servers with multiple IP addresses (multi-homed) if the primary DNS server only allows zone transfers from a specific IP address.

- **Send DNS requests from port number**\
    Specify if Simple DNS Plus should use a new random port number for each outbound request, or send all outbound requests from the same port number.\
    Using random port numbers helps protect against DNS spoofing attacks. For details see [How to secure you server / DNS spoofing](ht_secure.md#spoofing).\
    Using a fixed port number is not recommend unless the DNS server is not offering recursion or it is forwarding to another secure DNS server for all domains.

- **Use EDNS**\
    The original DNS specifications limits DNS request and response packets over UDP to 512 bytes (payload).
    As DNS servers need to send more data (longer IPv6 addresses, DNSSEC signatures, etc.) this limitation causes truncation and DNS servers have to switch to the less efficient TCP protocol.\
    With this option enabled, Simple DNS Plus will indicate to other DNS servers that it is able to receive larger packets over UDP (supported by most networks and Internet connections today).\  
    The packet size is configured using "EDNS maximum UDP payload size" under [DNS / Miscellaneous](wd_opt_dnsmisc.md) (used for both outbound requests and outbound responses).\
    Note that some older Cisco PIX firewalls and other firewall products may drop DNS packets with EDNS. If you experience this problem, please contact your firewall vendor to get a firmware update.
