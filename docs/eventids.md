---
Slug: event-ids-error-messages
Keywords: Event IDs,Error messages,Warning messages
DocID: 18
---
# Event IDs / Error Messages

Simple DNS Plus may write the following event IDs to the Windows Event Log (enabled in the [Options dialog / Logging / Windows Event Log section](wd_opt_winevent.md)), and log associated messages in the log files / Active Log View:

## Error Events

The following are recorded as "Error events" to the Windows Event Log, and appear in the Simple DNS Plus logs with a **\*\*\* Error:** prefix:


- **101 - Could not start DNS service on \<ip-address\> [port \<port\>] (\<error message\>)**\
    This usually means that another DNS server or another program is occupying the DNS port (53) on the same computer. Can also occur when using "Internet Connection Sharing".\
    For more information, please see [KB47](https://simpledns.plus/kb/47)\
    Once you have corrected the problem, use "Start server" from the File menu.

- **103 - Could not start HTTP API on port \<ip-address\> port \<port-number\> (error message)**\
    This usually means that the HTTP port is occupied by another program or possibly another instance of Simple DNS Plus.\
    You may need to change the port number used for HTTP in the [Options dialog / HTTP API](wd_opt_httpapi.md) section.

- **105 - Failed to start remote management on \<ip-address\> port \<port\> (error message)**\
    This usually means that the remote management port is occupied by another program or possibly another instance of Simple DNS Plus.\
    You may need to change the port number used for HTTP in the [Options dialog / Remote Management](wd_opt_remote.md) section.

- **203 - Could not save zone \<zone-name\> to zone file \<file-name\> - \<error message\>**\
    Another program may be accessing the zone file, the hard disk may be full, or something else is preventing Simple DNS Plus write access to the file.

- **251 - Failed to load plug-in \<plug-in instance display name\>: \<error message\>**\
    A [plug-in](pi_overview.md) could not be loaded.

- **257 - Error calling "\<method name\>" for plug-in "\<plug-in instance display name\>": \<error message\>**\
    An exception was throw executing a [plug-in](pi_overview.md) method.

- **258 - Asynchronous operation error in plug-in "\<plug-in instance display name\>": \<error message\>**\
    An exception was throw while a [plug-in](pi_overview.md) was executing something in a separate thread.

- **999 - Application error: [\<error-description\>]**\
    In the unlikely event that you should see this error message, please contact [support@simpledns.plus](mailto:support@simpledns.plus) for assistance.

## Warning Events

The following are recorded as "Warning events" to the Windows Event Log, and appear in the Simple DNS Plus logs with a **\*\*\* Warning:** prefix:

- **140 - Open DNS Server. Limiting recursion to trusted IP addresses is recommended (Options dialog / DNS / Resolver / Recursion)**\
    See the "DNS spoofing" and "Recursion" sections in [How to secure your server](ht_secure.md).

- **201 - Could not open zone file for \<zone-name\> from \<file-name\> - \<error message\>**\
    Another program may be accessing the zone file.

- **259 - Tread queue error for plug-in "\<plug-in instance display name\>": \<error message\>**\
    A problem related to queuing threads for plug-in processing.

- **302 - IP address \<ip-address\> blocked (more than \<n\> DNS requests per second)**\
    See the "Denial of service" section in [How to secure your server](ht_secure.md).

- **303 - Request from \<ip-address\> for BIND version**\
    See the "BIND version requests" section in [How to secure your server](ht_secure.md).

- **305 - TCP connection request from \<ip-address\> ignored - Exceeds maximum connections (\<n\>)**\
    See the "Denial of service (DoS)" section in [How to secure your server](ht_secure.md).

- **310 - Could not refresh zone \<zone-name\> from primary IP \<ip-address\> - Not configured to send outbound requests via \<IPv4/IPv6\>**\
    A secondary zone is configured to use a primary server IP address for which the IP version is not enabled in the [Options dialog / DNS / Outbound Requests section](wd_opt_dnsout.md).

- **311 - Socket error accepting TCP DNS connection: \<error code / message\>**\
    An exception was thrown while some attempted to establish a TCP connection with this server.

- **401 - Lame delegation for \<zone-name\> on this server (\<ip-address\>)**\
    A "Lame delegation" is when a DNS server, which is listed in the domain registration for a domain, is not configured with data for that domain.\
    "Lame delegation" sometimes happen because someone has registered a domain but only has one or no DNS servers, so they simply specify some random DNS servers to act as place-holders, even though none of these servers have a zone defined for the domain in question. Hence the domain is "lame" without a leg to stand on.\
    If you see this message about your own server ("this server"), you should take steps to correct this immediately.\
    If the domain-name in question is not yours, do a WHOIS [look up](wd_lookup.md) to determine the owner, and contact them to change it immediately (they are causing additional traffic on your Internet connection and additional processing for your DNS server ).\
    If the domain-name is yours - [add the zone](wd_newzone.md) to your server immediately.

- **501 - Notify request not sent to \<server-name\> for \<zone-name\> - Could not resolve IP address**\
    Changes were made to a primary zone on this server, but the server could not notify (see [zone transfers](df_zonetransfer.md)) a secondary DNS server.\
    This typically means that no [A-record](rec_a.md) is available for the DNS server name specified in the [NS-record](rec_ns.md) for the secondary DNS server.

- **502 - [\<server-name\>] [\<ip-address\>] did not respond to Notify request for \<zone-name\>**\
    Changes were made to a primary zone on this server, but the server did not get any response when trying to notify a secondary DNS server.\
    This typically means that the secondary server is down, or there is some type of network problem.

- **503 - Failed to Zone Transfer \<zone-name\> [and \<n\> other zones] from \<ip-address\> (\<error-description\>)**\
    This server (secondary) could not complete a [zone transfer](df_zonetransfer.md) from the primary DNS server.\
    This could be caused by general network problems or [security](ht_secure.md) settings on the primary server.\
    The server will continuously retry the zone transfer.

- **504 - Received zone transfer for "\<zone-name\>" from \<ip-address\> with [lesser SOA-record serial# \<serial\> (was \<serial\>)][conflicting record data]. Zone history wiped to avoid conflicts.**\
    Data on primary server might have been corrupted, or zone updated manually.

- **601 - Forward server \<ip-address\> does not offer recursion**\
    One of the forward DNS servers specified in the [Options dialog](wd_options.md) does not offer [recursion](df_recursion.md).\
    Select a different forward DNS server, or disable forwarding (not needed in most cases).

- **701 - Error opening log file - \<error-description\>**\
    There was a problem writing a log file to disk. The server has temporarily stopped writing to this log file, and will attempt to open the file again in 5 minutes.

- **702 - Error writing to log file - \<error-description\>**\
    There was a problem writing a log file to disk. The server has temporarily stopped writing to this log file, and will attempt to open the file again in 5 minutes.

- **703 - Error opening raw log file - \<error-description\>**\
    There was a problem writing the raw log file to disk. The server has temporarily stopped writing to this log file, and will attempt to open the file again in 5 minutes.

- **704 - Error writing to raw log file - \<error-description\>**\
    There was a problem writing the raw log file to disk. The server has temporarily stopped writing to this log file, and will attempt to open the file again in 5 minutes.

- **801 - Failed to automatically DNSSEC sign zone \<zone-name\> - \<error\>**\
    There was a problem DNSSEC signing a zone.\
    You need to update the zone records or the on-line DNSSEC keys for the zone.

## Information Events

The following are recorded as "Information events" to the Windows Event Log, and appear in the Simple DNS Plus logs without any prefix:

- **1 - DNS service started on \<ip-address\> port \<port\>**

- **2 - Server paused**

- **3 - Server shut down**

See also: [How to read the log](ht_readlog.md)
