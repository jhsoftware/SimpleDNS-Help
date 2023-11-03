---
Slug: definition-round-robin
Keywords: Round robin
DocID: 12
---
# Definition - Round Robin

Round Robin is a method of managing server (web, ftp, mail etc.) congestion by distributing connection load across multiple servers containing identical content.

Round robin works on a rotating basis in that one record is handed out, then moves to the back of the list; the next record is handed out, then it moves to the end of the list; and so on, depending on the number of servers being used. This works in a looping fashion.

Let's say a company has one domain name and with identical web pages residing on three separate web servers with three different IP addresses. When one user accesses the home page she will be sent to the first IP address. The second user who accesses the home page will be sent to the next IP address, and the third user will be sent to the third IP address. In each case, once the IP address is given out, it goes to the end of the list. The fourth user, therefore, will be sent to the first IP address and so forth.

Round Robin is enabled in the [Options dialog / DNS / Miscellaneous](wd_opt_dnsmisc.md) section.

Round Robin kicks in whenever two or more records with the same name and type exist in your own records or [cached](df_cache.md) data - such as two [A-records](rec_a.md) with identical names (but different IP addresses).
