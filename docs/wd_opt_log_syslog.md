---
Slug: options-dialog-logging-syslog-server
Keywords: Syslog
DocID: 95
---
# Options dialog - Logging - Syslog Server

- **Send log data to Syslog server**\
When this option is enabled, Simple DNS Plus will send log data to a syslog server using the standard syslog protocol ([RFC3164](https://www.rfc-editor.org/rfc/rfc3164.txt)).\
This can be useful for centralizing logging and/or taking advantage of various alerting and highlighting features of syslog server software.\
Many different syslog server software packages are available for various operating systems. An example for Windows is the "Kiwi Syslog Daemon" from [Kiwi Enterprises](https://www.kiwisyslog.com).

    - **IP address**\
    The IP address of the syslog server.

    - **UDP port**\
    The UDP port number of the syslog server.\
    The default value and standard UDP port number for syslog servers is 514. 

    - **Send test data**\
    Click this button to send a test log message to the syslog server at the IP address and UDP port above.
