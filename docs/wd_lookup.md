---
Slug: dns-look-up-window
Keywords: DNS Look Up,Look Up Window
DocID: 70
---
# DNS Look Up window

Use this tool to perform lookups against the local and/or other DNS servers.

See [Look Up Types](wd_lookup_types.md) for details.

The DNS Look Up window consists of a [Menu](wd_lookup.md#menu), a [Toolbar](wd_lookup.md#toolbar), [Domain name entry field](wd_lookup.md#entry), [Result display area](wd_lookup.md#result), an [Options pane](wd_lookup.md#options), and a [Status Bar](wd_lookup.md#status).

## Menu{#menu}

- **File menu**

    - **Look Up**\
    Choose one of the sub-items to do a specific [look up type](wd_lookup_types.md).

    - **Stop Query**\
    Cancel to current DNS look up.

    - **Exit**\
    Closes the DNS Look Up window.

- **Edit menu**

    - **Copy selection**\
    Copy the current selection in the [result display area](wd_lookup.md#result) to the Windows clipboard.

    - **Copy full response**\
    Copy everything in the [result display area](wd_lookup.md#result) to the Windows clipboard.

- **View menu**

    - **DNS/WHOIS Options**\
    Shows/hides the [Options pane](wd_lookup.md#options).

    - **IDN Native Characters**\
    Enables/disables display of native characters for [IDNs](df_idn.md).

    - **Toolbar**\
    Shows/hides the [toolbar](wd_lookup.md#toolbar).

    - **Status bar**\
    Shows/hides the [status bar](wd_lookup.md#status).

- **Help menu**

    - **Contents \& Index**\
    Opens this help file

    - **On-line support**\
    Opens the support web-page in your Internet browser.



## Toolbar{#toolbar}

- **Look Up button**\
    Choose one of the sub-items to do a specific [look up type](wd_lookup_types.md).

- **Stop button**\
    Cancel to current DNS look up.

- **Copy button**\
    Copy text from the [result display area](wd_lookup.md#result) to the Windows clipboard.

- **Options button**\
    Shows/hides the [Options pane](wd_lookup.md#options).

- **Help button**\
    Opens this help file



## Domain name entry field{#entry}

Enter the domain name or IP address to look up.

## Result area{#result}

Shows the result of the look up.

## Options pane{#options}

The Options pane is only visible (to the right of the result area) when enabled in the View menu or the Options button on the Tool Bar.

-  **DNS Options**

    - **Network protocol**\
    Choose between UDP, TCP (virtual circuit), [DNS over TLS (DoT)](df_dotdoh.md), and [DNS over HTTPS (DoH)](df_dotdoh.md).\
    Most DNS requests, except for zone transfers, are sent over UDP.\
    However in some situations it can beneficial to test if a DNS server also responds via TCP (which it should). This is also know as VC or "virtual circuit" in the classic NSLOOKUP command line tool.
    
    - **Query URL**\
    (Only available with the DNS over HTTPS (DoH) network protocol).\
    Specify the URL to send DNS requests to.
 
    - **HTTP method**\
    (Only available with the DNS over HTTPS (DoH) network protocol).\
    Choose GET or POST.\
    Also, POST requests are slightly smaller (fewer bytes sent on network), because the DNS request is attached in raw form, whereas it is encoded (Base64Url) with GET requests.
    Note that the HTTP method may affect HTTP caching if requests are routed through various (reverse) HTTP proxy servers.

    - **Server and port from Query URL**\
    (Only available with the DNS over HTTPS (DoH) network protocol).\
    When this is checked, the DNS server host name and port number taken from the Query URL. Otherwise you can specify them below.

    - **DNS Server**\
    Specify the host name or IP address of the DNS server to do the look up against.

    - **Port number**\
    The DNS server port number to do the look up against (standard is 53 for UDP/TCP, 853 for DoT, and 443 for DoH).
 
    - **Request recursion (RD flag)**\
    When checked (default), the DNS server will be asked to resolve the query if it doesn't have the answer in [cache](df_cache.md).\
    Not all DNS servers accepts requests for [recursion](df_recursion.md) (also an [option](wd_opt_dnsrecur.md) in the Simple DNS Plus).

    - **Include EDNS0 options**\
    When checked, the following EDNS0 (extended DNS) will be included in the DNS request.

        - **UDP payload size (bytes)**\
        Specify the maximum response packet size for UDP requests.\
        This can be useful for testing certain requests which return large response messages.\
        For example, IPv6 records were recently added for the Internet .com and .net top level names, making the full referral message for these domains larger than the standard 512 DNS message size.

        - **DNSSEC OK (DO flag)**\
        Ask the DNS server to return [DNSSEC](df_dnssec.md) signed data if available.

        - **Checking Disabled (CD flag)**\
        Ask the DNS server not to check [DNSSEC](df_dnssec.md) signatures.

- **WHOIS Options**

    - **WHOIS server**\
    Specify the host name or IP address of the WHOIS server to do the look up against.\
    If "Auto" is selected, the tool will automatically try to determine the server name / IP addresses.

    - **Port number**\
    The WHOIS server port number to do the look up against (usually 43).

    - **Response encoding**\
    A WHOIS response may be encoded in order to provide non-english characters or symbols.\
    If you see strange looking characters or question marks in the response text, try the lookup again with a different encoding.\
    The default selection (UTF-8 / ASCII) works with most WHOIS servers.



## Status Bar{#status}

Shows the current status of the look up process.
