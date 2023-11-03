---
Slug: new-zone-wizard
Keywords: New Zone Wizard,Zone
DocID: 73
---
# New Zone Wizard

The New Zone dialog is used to create a new [zone](df_zones.md) of one of the following types:

- **Primary Zone**\
    Creates a "master copy" in which you create records for your domain name.

- **Forward Zone**\
    Creates a new primary forward zone.\
You will be prompted to enter the zone name.\
See also the [Quick Zone Wizard](wd_quickdom.md) for even faster creation of primary forward zones.\
NOTE: You can create a private [root zone](df_root.md) by entering a single dot as the zone name - but only do this if your server is for an intranet and is not going to resolve any Internet domain names.

- **Reverse Zone**\
Creates a primary [reverse zone](df_reverse.md).\
NOTE: To create a secondary reverse zone, use the "Secondary Zone" option below.

    - **IPv4 (32 bit IP addresses)**\
    Creates a new primary reverse zone for IPv4 addresses.\
    You will be prompted to enter the first IP address, subnet mask and the zone name.\
    Enter the first IP address of your range of IP addresses and select the subnet mask according to the number of IP addresses you have.\
    If you have an IP address range of more than 256 IP addresses (class-C network), you should create a separate reverse zone for each class-C in that range. Reverse zones for larger subnets (/8 and /16) should only be use for delegations.\
    The zone name defaults to the standard [in-addr.arpa](df_reverse.md) name. For subnets other than 255.255.255.0 (full class-C), you can change the zone name - or use the "Look Up" button to automatically detect the reverse delegation name used by your IP provider.\
    After creating the zone, you can use the [Reverse zone IP-to-Name Mappings dialog](wd_iptoname.md) to edit the individual reverse records (reverse zones for 256 IP addresses or fewer).

    - **IPv6 (128 bit IP addresses)**\
    Creates a new primary reverse zone for IPv6 addresses.\
    You will be prompted to enter the first IP address and select a subnet mask bit size.\
    Enter the first IP address of your range of IP addresses and select the subnet mask bit size according to the number of IP addresses you have.

- **Secondary Zone**\
Creates a copy of a zone already configured on another primary DNS server for redundancy and load balancing. Records are created on the primary DNS server and automatically copied to this server through [zone transfers](df_zonetransfer.md).\
You will be prompted to enter the zone name, the IP address of the primary DNS server, and optionally a [TSIG key](df_tsig.md) for signing zone transfer requests.
