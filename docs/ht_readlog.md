---
Slug: how-to-read-the-log
Keywords: Log,Error messages,Warning messages,Header messages
DocID: 24
---
# How to read the log

You can open the "full text log files" created by Simple DNS Plus with notepad, or watch the most recent log entries using the [Active Log View](wd_views.md).

Log lines starting with "-\>" are details for a previous line.

Writing log files to disk can be activated in the [Options dialog / Logging / Log files](wd_opt_logfiles.md) section.

In addition to the logs, some events can be recorded to the Windows Event Log, which in turn can be used to send notification via network messages, e-mail, etc. See [Options dialog / Logging / Windows Event Log section](wd_opt_winevent.md).

## \*\*\* Error/Warning:... messages

For details and explanations see [Event IDs / Error Messages](eventids.md).

## \-\> Header:... messages

**-\> Header: Format Error**

Means that the DNS request was not formatted correctly.

This could be caused by network problems, a malfunctioning DNS server, or another network program incorrectly using the DNS port (53).

**-\> Header: Server Failure**

Usually means that a DNS server did not respond or that no [NS-record](rec_ns.md) (or associated [A-record](rec_a.md)) exists for a domain name.

Often follows the "\*\*\* Warning: Lame delegation..." message (see [Event IDs / Error Messages](eventids.md)).

This could also be caused by network connectivity problems.

**-\> Header: Non-Existent Domain**

Means that the domain name specified in the request does not exist.

If this happens for all outside domain names that you try to resolve, make sure you don't have a \<root\> zone in the [DNS Records window](wd_records.md).

**-\> Header: Not implemented**

Means that the DNS server does not support this type of query.

**-\> Header: Refused**

The queried DNS server refuses to respond to this query - usually due to local [security](ht_secure.md) settings.

This most often happens in connection with [zone transfers](df_zonetransfer.md) - make sure the primary DNS server allows the secondary servers to zone transfer the zone (see [Zone Properties dialog](wd_zoneprop.md)).

**-\> Header: Name exists when it should not**

This header is returned in a response to a [dynamic update](df_dyndns.md) request.

The update could not be completed because the prerequisites specified by the update request were not met.

**-\> Header: RR Set exists when it should not**

This header is returned in a response to a [dynamic update](df_dyndns.md) request.

The update could not be completed because the prerequisites specified by the update request were not met.

**-\> Header: RR Set that should exist does not**

This header is returned in a response to a [dynamic update](df_dyndns.md) request.

The update could not be completed because the prerequisites specified by the update request were not met.

**-\> Header: Server not authoritative for zone**

This header is returned in a response to a [dynamic update](df_dyndns.md) request.

The update could not be completed because the server responding is not configured with the zone specified in the update request.

**-\> Header: Name not contained in zone**

This header is returned in a response to a [dynamic update](df_dyndns.md) request.

The update could not be completed because the update name is not contained within the zone specified in the update request.

**-\> Header: TSIG Signature Failure**

This header is returned in a response to a [TSIG](df_tsig.md) signed [dynamic update](df_dyndns.md) or [zone transfer](df_zonetransfer.md) request.

The operation was not allowed because the TSIG signature in the update request was invalid.

**-\> Header: Key not recognized**

This header is returned in a response to a [TSIG](df_tsig.md) signed [dynamic update](df_dyndns.md) or [zone transfer](df_zonetransfer.md) request.

The operation was not allowed because the server responding is not configured with the TSIG key or signature algorithm used in the update request for the update name.

**-\> Header: Signature out of time window**

This header is returned in a response to a [TSIG](df_tsig.md) signed [dynamic update](df_dyndns.md) or [zone transfer](df_zonetransfer.md) request.

The operation was not allowed because the time stamp in the TSIG signature did not match the server's time (not within the requested "fudge" interval).
