---
Slug: options-dialog-remote-management
DocID: 96
---
# Options dialog - Remote Management

- **Enable Remote Management**\
Check this to allow remote management of this server.

    - **On IP address**\
    Select the local IP address that remote management clients connect to.

    - **TCP port**\
    Specify the TCP port number that remote management clients connect to.
    Note that the client connection dialog defaults to port 9053 when no port number is specified.

    - **Password**\
    Specify a password to authenticate remote management client.



**How to use this:**

You can manage the Simple DNS Plus service from a remote computer over your LAN or the Internet using the normal Simple DNS Plus user interface. This is faster and uses much less bandwidth compared to accessing a remote server via Remote Desktop, VNC, or similar.

Traffic between the server and the remote GUI is highly optimized and secure. Authentication uses SHA-1 challenge/response to prevent password sniffing, all data transferred is encrypted, and larger data chunks (such as zone files) are compressed.

To remote manage Simple DNS Plus, install Simple DNS Plus on the client computer (optionally without the core service), and use the "Remote Management" shortcut in the Windows Start menu - or run 

```
sdnsgui.exe -remote [remote-computer] [password]
```

or for the DNS Records window:

```
editrecs.exe -remote [remote-computer] [password]
```
