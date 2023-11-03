---
Slug: how-to-get-started
DocID: 26
---
# How to get started

A "DNS Server" has two core functions "DNS Resolver/Cache" and "Authoritative DNS Server".

Simple DNS Plus can be configured to do either one of these functions - or both.

## DNS Resolver/Cache

When a DNS server is configured as a DNS Resolver, it provides [recursive](df_recursion.md) domain name resolution to other computers.

This means that it is able to translate Internet domain names into IP addresses and the [reverse](df_reverse.md) (as well as providing other types of data) by sending queries to a number of different DNS servers on the Internet.

Simple DNS Plus [caches](df_cache.md) the information it learns along the way so that subsequent requests for the same information can be answered more quickly.

With the default Simple DNS Plus configuration, it is ready to work as a DNS resolver/cache.

To take advantage of this, you must configure the computers on the local network (including the one running Simple DNS Plus) to use the now local DNS server instead of DNS servers provided by your ISP.

This is done under the computer's Network TCP/IP properties by assigning the IP address of the computer running Simple DNS Plus as the DNS server.

The exact setup is slightly different for each version of Windows - illustrations are provided at <https://simpledns.plus/kb/26>

Alternatively, local computers (except the one running Simple DNS Plus) can be configured to get this configuration automatically using the DHCP Server [plug-in](pi_overview.md).

Next make sure Simple DNS Plus is running. Then test the configuration by opening a web-page such as <https://simpledns.plus>.

To ensure that you are not getting a copy cached by the browser, first empty out the browser cache (delete "Temporary Internet Files") and close all instances of the browser.

And if you are using Windows 2000 or later and have the "DNS Client" service running (the default), type "IPCONFIG /flushdns" at a command prompt to ensure that no DNS data is cached by this service.

If the expected web-site loads into your browser, everything is now working correctly.

You should also be seeing some activity in Simple DNS Plus ([Performance Graph](wd_views.md), the [Active Log](wd_views.md), and/or the request counter on the [status bar](wd_mainscreen.md#statusbar)).

If you are new to DNS it might be helpful to [examine the log files](ht_readlog.md) to get an idea how DNS requests are processed.

If you run Simple DNS Plus for a while, you should begin to notice an improvement in the time it takes to access web-pages - especially when you return to one you have visited previously.

This is [caching](df_cache.md) - your computers no longer must access an external DNS server every time you reopen a web-page.

## Authoritative DNS Server

The other core function of a DNS server is hosting domain names - a.k.a. [authoritative](df_authoritative.md) DNS server.

For more on this see [How to host a domain name](ht_hostdom.md).
