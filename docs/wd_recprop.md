---
Slug: record-properties-dialog
Keywords: * (Wilcard records),Wildcard records,Records properties
DocID: 103
---
# Record Properties dialog

The Record Properties dialog is used to specify a DNS record's name, data, [TTL](df_ttl.md), and comments.

**The record name** must be the same as or end with the name of the [zone](df_zones.md) it belongs to (automatically enforced), and can only be entered when creating a new record.\
To specify a wildcard record, enter an asterisk (\*) followed by a period (.) and the rest of the name.\
The asterisk can only be used as the first character, and only when immediately followed by a period.

**The record data** depends on the record type - see the individual [record types](rectypes.md) for more information.

**The "Record [TTL](df_ttl.md) (Time To Live)" field** specifies how long other DNS server and clients are allowed to [cache](df_cache.md) this record.

**The "Record comments" field** can be use to keep any additional information about the record such as what the record does, or a client account number.\
For records created or updated via dynamic updates or HTTP, Simple DNS Plus will automatically enter a comment about how and when the record was created.\
NOTE: This field is not transferred to secondary DNS servers through [zone transfers](df_zonetransfer.md).

For [A-Records](rec_a.md) and [AAAA-records](rec_aaaa.md) there is a special "Update Reverse Zone" option. This will create or update a [PTR-record](rec_ptr.md) in a [reverse zone](df_reverse.md) to enable reverse lookups on the IP address.
