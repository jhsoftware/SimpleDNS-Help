---
Slug: options-dialog-dns-nat-ip-alias-conversion
Keywords: NAT router,NAT to LAN,NAT IP Alias
DocID: 80
---
# Options dialog - DNS - NAT IP alias conversion

- **Enable NAT IP alias conversion for DNS requests from LAN**\
In DNS responses to DNS requests from LAN clients only, this function changes host records which are pointing to a public IP address of the NAT router to point to the corresponding private IP address of a local server.\
This way, for example, HTTP requests from LAN clients for local web-sites will go directly to the local web-server instead of via the NAT router.

    - **NAT router IP address mappings (aliases)**\
    Enter external / internal IP address pairs.

    - **LAN IP addresses (internal/private side of the NAT router)**\
    Enter the private/internal IP addresses/subnets of your local area network.

    - **This computer is on the LAN side of the NAT router**\
    Check if this computer is located on the LAN.


**How to use this:**

If you wish to run a web-server behind a NAT router, then you must point the DNS records for your web-site domain names to the public IP address of the NAT router, and on the NAT router map port 80 (for HTTP) to the private IP address of the local web-server computer.

This works fine for all external visitors from the Internet.
However, this setup often creates problems when you want to access your own web-site from the private side of the NAT router (from within the LAN).

Without this function, when your web-browser makes a DNS request for the web-site domain name, it gets your public IP address and then tries to make a HTTP connection to that IP address via the NAT router.

This requires the NAT router to route packets from the LAN side to the public IP address and back into the LAN - which many NAT routers cannot handle correctly. Often you get the router login page instead or nothing at all.
Even if this does work, you are putting unnecessary load on the router.

A "NAT Router" can be a physical device such as those from Cisco, Linksys, DLink, NetGear, etc., or a computer running "Internet Connection Sharing" or similar.

> [!BLUE] **Note**
>
> This function is for use with network setups with one or more external/public IP addresses on a NAT router mapped to internal server(s) on private IP addresses.
>
> This only works with **one-to-one IP address mappings** - each external/public IP address can only be mapped to a single internal/private IP address.
>
> If you need to have different ports on one external IP address mapped to different internal IP addresses, then you should run two DNS servers instead - one for external use and one for internal use.
