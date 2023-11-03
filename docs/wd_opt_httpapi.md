---
Slug: options-dialog-http-api
Keywords: HTTP API
DocID: 91
---
# Options dialog - HTTP API

- **Enable HTTP API interface**\
Check/uncheck to enable/disable this functionality.

    - **URL prefix**\
    The first part of the URL to listen for HTTP API requests on.\
    The simplest form is "http://\<local-ip-address\>:\<port\>". Defaults to `http://127.0.0.1:8053`.\
    The HTTP API uses the Windows HTTP Server API for serving HTTP request. This allows the HTTP API to share port 80 / 443 with IIS and other applications.\
    For details on the URL prefix format, see <https://msdn.microsoft.com/en-us/library/windows/desktop/aa364698(v=vs.85).aspx>\
    The HTTP API can be served securely via SSL by using a URL prefix starting with `https://`.\
    The easiest way to setup an SSL certificate for this, is if you are also running an SSL based web-site on IIS on the same computer as Simple DNS Plus, and you configure the HTTP API to be served under the same host name as that site (but under a sub-path). This way you can just manage the SSL certificate in IIS.\
    However, if you are NOT doing this or if you want to use a different SSL/TLS certificate for the HTTP API, you will need to "bind" an SSL/TLS certificate to the host name (and port) used. The "Bind SSL certificate" button will do this.

    - **Authentication**\
    How clients are authenticated - choose between "None (anonymous)", "Basic", "Digest", and "Integrated (NTLM / Kerberos)".\
    We highly recommend using Digest or Integrated for best security.

        - **Windows user account**\
        Check this to use a Window user account for authentication (password stored and controlled by Windows).\
        Always enabled when using "Integrated" authentication.

        - **User ID**\
        Specify the user ID to grant access.\
        If the "Windows user account" option above is enabled, this must be the user ID of an existing Windows user account.

        - **Password**\
        Specify the password.\
        Only available if "Windows user account" option above is not enabled.

    - **Enable CORS (Cross Origin Resource Sharing)**\
    Enabling this, allows you to access the Simple DNS Plus HTTP API with javascript on a web-page running in a browser.
    For more about CORS - see <https://en.wikipedia.org/wiki/Cross-origin_resource_sharing>
    
    - **Enable the HTTP API v. 1 for backwards compatibility**\
    We do NOT recommend enabling this unless you have existing systems/applications that rely on the original HTTP API (v. 1).\
    When this option is enabled, the original HTTP API (v. 1) will be at the URL specified under "URL Prefix", and the current HTTP API (v. 2) will be under "/v2/...".


See also: [How to use the HTTP API](ht_http.md).
