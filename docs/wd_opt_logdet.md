---
Slug: options-dialog-logging-log-details
Keywords: Log details
DocID: 92
---
# Options dialog - Logging - Log Details

- **Log individual requests, responses, and other events**\
Select this option to log DNS requests and other events.

    - **Include DNS record details**\
    When checked, DNS request activity will be logged at the record level.

    - **Include EDNS0 details (UDP payload size)**\
    When checked, the EDNS0 details of DNS requests and responses will be logged.

    - **Include outbound DNS requests**\
    When checked, outbound DNS requests (to resolve DNS) and associated responses are logged.

    - **Include requests from blocked IP addresses**\
    When checked, DNS requests from [blocked IP addresses](wd_block.md) will be logged.

- **Only log Errors and Warnings**\
Select this options to only log events for potential problems.

- **Log internationalized domain names (IDNs) in native characters**\
When checked, all [IDNs](df_idn.md) will be logged in native characters (log files are UTF8 encoded).

See also: [How to read the log](ht_readlog.md)
