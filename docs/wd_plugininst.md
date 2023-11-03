---
Slug: plug-in-instance-dialog
Keywords: Plug-In instance
DocID: 99
---
# Plug-In Instance dialog

**Plug-in instance display Name**\
This name is used to uniquely identify the plug-in instance.\
For plug-in types that have a [View](wd_views.md), this name will also appear in the [main window](wd_mainscreen.md) View menu and on the view tab.

Below the display name, there are 1, 2, or 3 tabs depending on the plug-in type:

- **Plug-In Settings tab**\
This tab is available for plug-ins that have unique settings (for plug-in developers: implements IOptionsUI).\
The content of this tab defines the behaviour of the plug-in and is different for each type of plug-in.

- **DNS Requests tab**\
This tab is available for all plug-ins that in some way process DNS requests (for plug-in developers: plug-ins not based on INoDNS).\
Specify when the plug-in should process a DNS request - either "Always", "Never", or "Only when...".\
With the default selection (Always), all DNS requests are processed by the plug-in.\
If the plug-in does a lot of work for each request (such as database lookups) it is recommended to limit this to specific domains, IP ranges, record types, etc. in order to optimize performance.\
With the later option (Only when...) you can construct a set of rules based on a combination of various properties of the DNS request etc.

- **Listed IP Addresses**\
This tab is available for plug-ins that in some way lists IP addresses (for plug-in developers: implements IListsIPAddress).

    - **Perform DNS recursion for IP addresses listed by this plug-in**\
    When enabled, Simple DNS Plus will resolve DNS requests received from IP addresses listed by this plug-in - even if they are not listed in the Options dialog / DNS / Recursion section.

    - **Whitelist IP addresses listed by this plug-in from all DNSBLs**\
    When enabled, Simple DNS Plus will respond to any DNS request for A-records for names starting with a reversed IP address, that is listed by this plug-in, with a "name does not exist" error code.\
    When a client computer (who's IP address is listed by this plug-in) sends an e-mail to a local e-mail server which is using this same Simple DNS Plus server, and this e-mail server looks up the sender's IP address (the client computer) in some DNSBL list, this option ensures that the result is always "not black listed".\
    This can be useful because dynamic IP address ranges are often black listed as e-mail senders.


See also: [Plug-Ins Overview](pi_overview.md)
