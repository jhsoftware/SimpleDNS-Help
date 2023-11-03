---
Slug: check-internet-delegations-dialog
DocID: 61
---
# Check Internet Delegations dialog

This feature lets you automatically test if the [NS-](rec_ns.md) and [SOA-records](rec_soa.md) in your local zone data match the actual current delegations on the Internet (the DNS server names listed in the domain name registrations).

This can be very useful both to check for errors and to make sure that you still own the domain names that you think you do.

It could also be used for example by ISPs to see if any customers have abandoned them (changed their DNS to another provider).

- **Test zones in all zone groups / Only test zones the zone group**\
Specify which zone group(s) to check zones from.

- **Test primary zones**\
Check this if primary zones should be tested.

- **Test secondary zones**\
Check this if secondary zones should be tested.

- **Test suspended zones**\
Check this if suspended zones should be tested.

- **Also test that each zone contains NS-records pointing to**

- **The name of this server (\<server name\>)**\
Compare zone's NS-record values to the local server's name.

- **The default secondary servers (see Default Zone Values dialog)**\
Compare zone's NS-record values to default secondary servers from [Default Zone Values dialog](wd_defzoneval.md).
