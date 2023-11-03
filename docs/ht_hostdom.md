---
Slug: how-to-host-a-domain-name
Keywords: Registrar,Hosting DNS
DocID: 20
---
# How to host a domain name

With Simple DNS Plus you can host DNS for your own domain names (and/or for others).

NOTE: This requires that you have a static Internet IP address. You cannot reliably host DNS on a dynamic IP address (such as a dialup connection).

First a domain name must the registered on the Internet.

You can use the "WHOIS" [look up](wd_lookup.md) function in Simple DNS Plus to determine if a domain name is available.

There is an ever growing number of companies (registrars) and resellers offering domain name registration for TLDs (top level domains) like ".com", ".net", ".org", and many more.

When registering a domain name (or modifying a registration), you have to specify which DNS servers will be responsible for the domain name (also referred to as "host records" - or [NS-records](rec_ns.md)).

Here you need to specify your own DNS server(s) by name - such as "ns1.example.com".

If you are already hosting other domain names you can use the existing "ns..." name for your server(s).

Otherwise you may have to first create these "host records" ("ns1.example.com" = IP address).

With some registrars you can do this as part of the domain name registration, others have a separate process for this.

When in doubt, contact your registrar for details.

NOTE: The registrar may do a DNS lookup to see if you have the DNS server name listed correctly on your DNS server. So before you use a new DNS servers name ("ns#.example.com") for the first time in a domain name registration, make sure to first setup an [NS-record](rec_ns.md) and associated [A-record](rec_a.md) for this in Simple DNS Plus.

It may take several days for a new domain name and changes to become fully active on the Internet (most are typically active within a few hours).

This delay is caused by the process of updating the top level DNS servers (the Internet DNS servers responsible for ".com" and other top level domains) with the new information for your domain name.

You can configure your domain name in Simple DNS Plus even before you have registered it and use it yourself, but other people on the Internet won't be able to access it before it is registered and active.

Next you need to configure the domain in Simple DNS Plus.

From the [main window](wd_mainscreen.md), click the "Records" button.

You should now be in the [DNS Records window](wd_records.md). This is where you work with your domain names and records.

The easiest way to configure a new domain name is through the [Quick Zone Wizard](wd_quickdom.md) which is activated with the "Quick" button.

Simply enter the domain name, and the IP addresses of your web, mail, and FTP servers (all optional) and click the OK button.

Now your domain name is ready to go!

NOTE: A "zone" basically represents a domain name and any sub-names under it - see [zone definition](df_zones.md) for details.

Depending on your own requirements and the requirements of your registrar, you may also need to [setup a secondary DNS server](ht_primsec.md).
