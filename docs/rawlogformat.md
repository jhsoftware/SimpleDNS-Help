---
Slug: raw-log-file-format
Keywords: sdraw,Raw log file format
DocID: 28
---
# Raw log file format

Simple DNS Plus raw log files (.sdraw) contain an entry for each received DNS request as follows:

|**Bytes**|**Description**
|---|---
|3|Number of seconds since midnight \*
|2|DNS request packet bytes 3 and 4 (header flags)
|2|Query type \*
|2|Query class \*
|1|Length of query name less 1
|variable|Query domain name (DNS packet format)
|1|Length of request source IP address (IPv4=4, IPv6=16)
|variable|Request source IP address

\* bytes represent integer value in network byte order (most significant byte first / big-endian).

A command line tool "Filter Raw Log" is available to extract and filter raw log data - [more information](https://github.com/jhsoftware/SDNSFilterRawLog/blob/master/README.md).

And a .NET programming library "Raw Log Library" is available for accessing raw log data programmatically - [more information](https://github.com/jhsoftware/SDNSRawLogDLL/blob/master/README.md).

Raw request logging is enabled in the [Options dialog / Logging / Log Files section](wd_opt_logfiles.md).
