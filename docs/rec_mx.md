---
Slug: mx-records
Keywords: MX record type,Mail exchange,Mail server
DocID: 44
---
# MX-Records (Mail exchange)

MX-records are used to specify the e-mail server(s) responsible for a domain name.

Each MX-record points to the name of an e-mail server and holds a preference number for that server.

If a domain name is handled by multiple e-mail servers (for backup/redundancy), a separate MX-record is used for each e-mail server, and the preference numbers then determine in which order (lower numbers first) these servers should be used by other e-mail servers.

If a domain name is handled by a single e-mail server, only one MX-record is needed and the preference number does not matter.

When sending an e-mail to "user@example.com", your e-mail server must first look up any MX-records for "example.com" to see which e-mail servers handles incoming e-mail for "example.com".

This could be "mail.example.com" or someone else's mail server like "mail.isp.com".

After this it looks up the [A-record](rec_a.md) for that e-mail server name to connect to its IP-address.

> [!YELLOW] **Important**
>
> An MX-record must point to the name of a mail server - not directly to the IP-address.\
> Because of this, it is very important that an [A-record](rec_a.md) for the referenced mail server name exists (not necessarily on your DNS server, but wherever it belongs), otherwise there may not be any way to connect to that e-mail server.

Do not point an MX-record to a [CNAME-record](rec_cname.md). Many e-mail servers don't understand this. Add another [A-record](rec_a.md) instead.

To create a new MX-record, right-click a zone in the left list in the [DNS Records window](wd_records.md), and select "New MX-record" from the pop-up menu.

This record type is defined in [RFC1035](http://www.rfc-editor.org/rfc/rfc1035.txt).
