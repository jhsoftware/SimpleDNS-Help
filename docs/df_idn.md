---
Slug: definition-internationalized-domain-names-idns
Keywords: Internationalize domain names,IDN
DocID: 8
---
# Definition - Internationalized domain names (IDNs)

Technically the DNS protocol is limited to standard ASCII characters (byte values 0-127), which does not include any non-english characters.

However in many end-user applications, like browsers, it is possible to use domain names containing non-english characters - so called "internationalized domain names" or "IDNs".

This is done by puny-encoding ([RFC3492](http://www.rfc-editor.org/rfc/rfc3492.txt)) the IDN behind the scenes so that the domain name sent to the DNS server and web-server is in an encoded form containing only the standard characters allowed in the DNS protocol.

Puny-encoded domain name segments (between dots) always starts with "xn--".

Each domain name segment is encoded separately, and only domain names segments which contain international characters are encoded.

You can say that an IDN has two display forms:
- "native character form" containing international characters.
- "puny-encoded form" containing only ASCII characters and where some or all segments start with "xn--".

For example, if you enter the domain name ![](/images/idn.gif) (www.tokyo.net in Japanese) into FireFox or IE7, the browser will convert this into "www.xn--1lqs71d.net" (the puny-encoded form) before sending it to the DNS server and web-server.

It is important to note that the server (DNS, web, etc.) will only see the puny-encoded form of the IDN, not the native character form entered by the user.

So if the server software does not have direct support for IDNs, you must use the puny-encoded form of the IDN when configuring the server software, for example, when setting up a web-site in IIS or Apache.

Simple DNS Plus has direct support for IDNs and automatically converts IDNs to the puny-coded form behind the scenes.

You can enter IDNs in either form (native characters / puny-encoded). Both ways will result in the same data and works equally well.

You can choose to display IDNs in either form in the [DNS Records](wd_records.md), [DNS Look Up](wd_lookup.md), [DNS Cache Snapshot](wd_snapshot.md) windows through the View menu / IDN Native Characters function in each of those windows.

You can also choose in which form to log IDNs in DNS requests and responses.

See [Options dialog / Logging / Log Details](wd_opt_logdet.md) section.
