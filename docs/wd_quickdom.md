---
Slug: quick-zone-wizard
Keywords: Quick Zone Wizard
DocID: 101
---
# Quick Zone Wizard

The Quick Zone Wizard automatically creates a new [zone](df_zones.md) with some pre-defined DNS records.

The standard default template contains the following variables / entry fields.

Replace "example.com" in the following with your own domain name:

- **Domain Name**\
    Enter your domain name "example.com" (without the "www." prefix).

- **Web server IP** (optional)\
    Enter the IP address of the web server for this domain name.\
    The wizard creates an [A-record](rec_a.md) for "example.com" with this IP address, and a [CNAME-record](rec_cname.md) for "www.example.com" pointing to "example.com".\
    This allows visitors to access your web-site through both "www.example.com" and just "example.com".

- **Mail server IP** (optional)\
    Enter the IP address of the e-mail server for this domain.\
    The wizard creates an [MX-record](rec_mx.md) for "example.com" pointing to "mail.example.com", and an [A-record](rec_a.md) for "mail.example.com" with this IP address.\

- **FTP server IP** (optional)\
    Enter the IP address of the FTP server for this domain.\
    The wizard creates an [A-record](rec_a.md) for "ftp.example.com" with this IP address.

The wizard also automatically creates an [NS-record](rec_ns.md) for the primary DNS server (this server), and a [SOA-record](rec_soa.md) and [NS-records](rec_ns.md) for secondary DNS servers as defined in the [Default Zone Values dialog](wd_defzoneval.md).

Clicking the "Use as Default" button will save the current values with the template and these values will automatically appear the next time you use the same Quick Zone Wizard template.

The Quick Zone Wizard is template based and supports multiple templates through a drop-down menu on the "Quick" button.

It is possible to modify the default template as well as adding your own templates. For details see <https://simpledns.plus/kb/116>
