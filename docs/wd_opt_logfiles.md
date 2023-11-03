---
Slug: options-dialog-logging-log-files
Keywords: Log files,Raw log
DocID: 93
---
# Options dialog - Logging - Log Files

- **Full text log files**\
When enabled, Simple DNS Plus will write all DNS queries and responses to a log file.

    - **Begin new log file**\
    Select how often a new log file should be created.

    - **Recycle log files**\
    To conserve disk space select how often the log files should be recycled (overwritten with new data).\
    Log files can grow very big very fast. Recycling them is a good way to conserve hard disk space.

- **Raw log files (incoming DNS requests only)**\
When enabled, Simple DNS Plus will create additional "raw" log files of all incoming DNS requests.\
This can be used to create domain / usage statistics and other purposes.\
A command line tool "Filter Raw Log" is available to extract and filter raw log data - [more information](https://github.com/jhsoftware/SDNSFilterRawLog/blob/master/README.md).\
And a .NET programming library "Raw Log Library" is available for accessing raw log data programmatically - [more information](https://github.com/jhsoftware/SDNSRawLogDLL/blob/master/README.md).\
See [Raw log file format](rawlogformat.md)

- **HTTP API debugging log files (one file per HTTP request)**\
When enabled, Simple DNS Plus writes full headers and payload of each HTTP API request to an individual log file.\
Use this to see the exact details of HTTP API client requests, for debugging purposes.\
Note that enabling this will potentially create a lot of log files with a lot of data. Therefore this should only be enabled while debugging HTTP API client code.

- **Location of log files**\
Specify the directory where log files are written.\
Just like with other log files, system performance can be enhanced by writing log files to different physical disk drive (other than where the operating system is installed).\
NOTE: Do not use a network drive location for this - because the Simple DNS Plus service runs under the SYSTEM account and therefore does not have access to network shares.
