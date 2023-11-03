---
Slug: definition-caching
Keywords: DNS Cache,Caching
DocID: 2
---
# Definition - Caching

Each time a [recursive](df_recursion.md) DNS request is made to Simple DNS Plus, it caches (stores in memory) the different DNS records it comes across while searching for the requested records.

The cached DNS records are then used to locate information faster for following DNS requests.

By default, cached DNS records are stored until they time-out based on their [TTL](df_ttl.md).

Most DNS servers will not cache a DNS record for more than one week. This is also the default in Simple DNS Plus, but you can change this through the "Maximum cache time" option.

To view a [snapshot](wd_snapshot.md) of the currently cached records, from the [main window](wd_mainscreen.md) click the "Cache" button or press F4.

To empty the cache:

- from the [main window](wd_mainscreen.md) select File menu - \> Clear DNS Cache
- Or use the "-C" [command line option](ht_cmdline.md).
- Or use the "clearcache" [HTTP API](ht_http.md) command.

You can change the various options related to DNS caching in the [Options dialog / DNS / Resolver / DNS caching](wd_opt_dnscaching.md) section.
