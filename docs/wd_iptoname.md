---
Slug: reverse-zone-ip-to-name-mappings-dialog
Keywords: Reverse Zone Wizard,IP-to-Name Mappings
DocID: 69
---
# Reverse zone IP-to-Name Mappings dialog

Use this dialog to edit an existing [reverse zone](df_reverse.md) without having to deal with "in-addr.arpa", reversing IP addresses etc.

To edit a record (IP to domain name), simply enter the corresponding domain name next to an IP address.

The fastest way to populate all the records is the "Auto Fill" function.

Enter a domain name, and all the records will be filled with something like "1-2-3-4.example.com", based on the IP addresses.

The "Auto Scan" function automatically populates the reverse records by scanning all forward zones for [A-records](rec_a.md) with IP addresses belonging to this reverse zone.

To create a new reverse zone, use the [New Zone](wd_newzone.md) function.
