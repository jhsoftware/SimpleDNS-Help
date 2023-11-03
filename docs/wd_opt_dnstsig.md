---
Slug: options-dialog-dns-local-zones-tsig-updates
Keywords: TSIG Dynamic Updates
DocID: 88
---
# Options dialog - DNS - Local Zones - TSIG Updates

Simple DNS Plus accepts [dynamic update](df_dyndns.md) requests signed with [TSIG keys](df_tsig.md) in this list.

You should configure a unique TSIG key for each client making dynamic updates.

You can specify which domain names (in local zones) that the client may update for each key.

TSIG signed dynamic updates can be used directly with several "DynDNS" client programs - see <https://simpledns.plus/kb/40>

Alternatively you can use the DynDNS Service [plug-in](pi_overview.md) - see <https://simpledns.plus/kb/173>

This plug-in also supports several HTTP based update methods and is specifically targeted towards "DynDNS" scenarios (computers with dynamic IP addresses on the Internet). However it only supports updates for host records (A-records).

TSIG signed dynamic updates (this section of the Options dialog) allows more advanced updates (any record type, multiple records in a single update, deletions, etc.) and greater flexibility in which records each client/key may update - but only through the DNS protocol (not HTTP).
