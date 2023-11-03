---
Slug: how-to-use-the-http-api
Keywords: HTTP API
DocID: 21
---
# How to use the HTTP API

Simple DNS Plus includes a HTTP API through which you can perform most of the operations that are available through the GUI.

The HTTP API is [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) based and data is generally exchanged in [JSON](https://en.wikipedia.org/wiki/JSON) format.

This HTTP API is not intended as a direct user interface, but rather a way to communicate with Simple DNS Plus from other applications over the network. For example ASP pages running on IIS, PHP pages on Apache, javascript running on a browser, etc.

By default, Simple DNS Plus listens for HTTP requests on IP address 127.0.0.1 port 8053. 
With this default configuration, you can open the HTTP API "home page" in your browser using <http://127.0.0.1:8053>. 
There you will find a link to the HTTP API specification file ([Swagger](http://swagger.io/) / OpenAPI format) that you can use to explore and test the HTTP API.

You can change these setting in the [Options dialog / HTTP API section](wd_opt_httpapi.md).

### CORS support

If you want to access the HTTP API with javascript running on a web-page, you need to enable and configure [CORS](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing). You do this in the [Options dialog / HTTP API section](wd_opt_httpapi.md).

### SSL

The HTTP API can be served securely via SSL (https://...). 

The easiest way to setup an SSL certificate for this, is if you are also running an SSL based web-site on IIS on the same computer as Simple DNS Plus, and you configure the HTTP API to be served under the same host name as that site (but under a sub-path). This way you can just manage the SSL certificate in IIS.\
If you are not doing this or if you want to use a different SSL/TLS certificate for the HTTP API, you will need to "bind" an SSL/TLS certificate to the host name (and port) used. There is a "Bind SSL certificate" button in the [Options dialog / HTTP API section](wd_opt_httpapi.md) to do this.


### Debugging log files

To see the exact details of HTTP API client requests, you can enable this in
the [Options dialog / Logging / Log files section](wd_opt_logfiles.md) / "Write HTTP API debugging log files (one file per HTTP request)".

WARNING: This can quickly add up to a lot of log files and data. Make sure to only enable this when needed.
