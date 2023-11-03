---
Slug: definition-ttl-time-to-live
Keywords: TTL,Time To Live
DocID: 15
---
# Definition - TTL (Time To Live)

All DNS records have a TTL (Time To Live) property, specifying the maximum amount of time other DNS servers and applications may cache the record.

Setting a DNS record's TTL value to zero, means that applications and DNS servers must not cache the record.

When a DNS record is stored in the cache of a DNS server, the record's TTL is continuously reduced as time go by, and when the TTL finally reaches zero the record is removed from the cache.

When a DNS server passes DNS records from the cache along to applications and other DNS servers, it supplies the current TTL value - not the original. This way the original TTL is guaranteed no matter how many DNS servers the record passes through.

When deciding on the TTL, you need to consider how often the record will be updated.

Because of caching, changes to a DNS record will not reach the entire network until the original TTL has expired - a good reason for setting a short TTL.

However caching helps reduce network traffic. The longer the TTL, the longer the record will live in other DNS server caches around the world, and so fewer requests to the original DNS server are needed - a good reason for setting a long TTL.

Generally, for a record pointing to a server/device with a static IP address and no need for quick updates, a TTL value of one day is a good starting point.

However, if the record is for a host with a dynamic IP address or for server which is part of some kind of failover set, you should be using a TTL value of a few minutes or less.

Most DNS servers will not cache a DNS record for more than one week. This is also the default in Simple DNS Plus, but you can change this through the "Maximum cache time" option - see [Options dialog / DNS / Resolver / Caching section](wd_opt_dnscaching.md).

Use the [Record Properties dialog](wd_recprop.md) to modify a record's TTL (select the record in the [DNS Records window](wd_records.md) and click the "Properties" button).

See also: [Caching](df_cache.md)
