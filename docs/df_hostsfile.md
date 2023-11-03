---
Slug: definition-hosts-file
Keywords: Hosts File
DocID: 7
---
# Definition - Hosts File

Before DNS servers were invented, domain name translation depended entirely on the "hosts file", a text file stored on a server or the PC. The hosts file listed, line by line, Internet domain names and their associated IP addresses. The "master hosts file" was compiled and stored on the machines at the Internet "NIC" and was downloaded on a regular basis by everyone accessing the Internet (not many at the time). Obviously this hosts file quickly grew much to large too be manageable. As the Internet grows, new domain names are added by the minute, and it is impossible for every computer on the Internet to keep downloading this file.

The solution of course was the DNS server system. Unlike the hosts file, DNS servers don't rely on a single large mapping file. Instead DNS servers only contain information about the domain names they are directly responsible for and some limited reference data on how to find other domain names.

Computers can still use the "hosts" file for name to IP-address translation instead of DNS, and this works fine on a small network where there are few changes and a limited number of computers to maintain.

On Windows computers, the "hosts" file is located in "c:\windows\system32\drivers\etc".

Please note that the hosts file must be named "hosts" without any extension and it must be located in the above directories for Windows to automatically use it without a DNS server.

One popular use of hosts files today is to block banner ads and other unwanted Internet content.

For example, pointing "ad-images.example.com" to 127.0.0.1, would prevent anything including banner ad images from being downloaded from that domain.

This may also help to conserve bandwidth and actually make Internet surfing significantly faster.

Some web-sites offer hosts file for download with updated lists of ad servers, malicious contents, etc.

With Simple DNS Plus you can easily share one or more hosts file between all computers on your local network using the Hosts File [plug-in](pi_overview.md) making it easy to maintain this in just one place.
