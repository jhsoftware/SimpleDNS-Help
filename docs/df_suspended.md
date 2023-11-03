---
Slug: definition-suspended-zone
Keywords: Suspended Zone
DocID: 13
---
# Definition - Suspended Zone

Suspending a zone allows you to temporarily stop serving data for a a [zone](df_zones.md) without deleting the zone.

This can be useful for example if you are hosting the domain name for someone else, and they forgot to pay the bill...

You can suspend / resume zones in the [DNS Records window](wd_records.md) by right-clicking a zone in the left list and selecting Suspend / Resume from the pop-up menu.

A suspended zone is indicated by a "paused" icon and a red zone name.

How Simple DNS Plus responds (or not) to DNS requests for names in a suspended zone depends on the settings in the [Options dialog / DNS / Local Zones / Suspended Zones](wd_opt_dnssusp.md) section.

When you suspend or resume a zone on a "super master" server, the zone's suspended status is automatically transferred to all Simple DNS Plus "super slave" servers. For more on "Super Master/Slave" see[ Options dialog / DNS / Local Zones / Super Master/Slave](wd_opt_dnsms.md) section.

If the secondary server is not Simple DNS Plus or if you are not using the Super Master/Slave feature, you need to remember to suspend/resume the zone on both primary and secondary DNS servers.
