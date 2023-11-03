---
Slug: options-dialog-dns-non-existing-domains
Keywords: NXDOMAIN redirect,Non-existing domains
DocID: 82
---
# Options dialog - DNS - Non-existing Domains

- **Redirect requests for non-existing domain names**

    - **Requests for A-records (IPv4)**\
    Enter the IP address to redirect to.

    - **Requests for AAAA-records (IPv6)**\
    Enter the IP address to redirect to.

    - **Additional TXT-record explaining synthesized response**\
    Enter a short text explaining why the client is being redirected.\
    This will be visible when someone uses diagnostics tools such as NSLOOKUP, DIG, and other DNS lookup tools.

    - **Exceptions...**\
    Click this button to specify the following exceptions:

        - **Only redirect domain names starting with 'www'**\
        Limit redirection to typical web-site domain names.

        - **Do not redirect domain names that belong to local zones (authoritative)**\
        Limit redirection to domain names other than your own.

        - **Do not redirect domain names that begin with an IPv4 address (reverse and RBL/DNSBL record names)**\
        When checked, domain names where the first 4 name segments resemble an IPv4 address will not be redirected.\
        WARNING: If your e-mail server or spam filter programs are using one or more RBL/DNSBL lists, redirecting non-existing domain names representing RBL/DNSBL records could cause e-mails from valid senders to be rejected. We therefore recommend enabling this exception (default).

        - **Do not redirect these domain names and their sub-names**\
        Limit redirection to domain names other than these.

        - **Do not redirect queries from the following IP addresses**\
        Limit redirection to queries from other IP addresses than these.

**How to use this:**

Typically when you enter a non-existing domain name in a web-browser, you either get an error page, or you are redirected to some search web-site controlled by the web-browser company or possibly your ISP.

This of course happens all the time because of misspellings and bad links on web-sites.

Now you can take advantage of those failed requests (from any client configured to use your DNS server) by redirecting them to your web-server instead of giving this traffic to the browser companies.

This option redirects all [recursive](df_recursion.md) DNS requests for non-existing domain names to a server IP address which you control.

This gives you a unique opportunity to present your own custom search page, a domain sale offer, a marketing message, an intranet site, or anything else you can think of.

> [!YELLOW] **Warning**
>
>This function redirects **ALL** DNS requests for non-existing domain names (it is not possible for the DNS server to tell if a DNS request comes from a browser or another type of application), so you may need to use the exceptions options to limit this.
>
> For example you may want to setup an exception for the IP address of your e-mail server so it won't try to deliver (otherwise failed) e-mails to your web-server's IP address.

> [!BLUE] **Note**
>
> Only requests which are for domain names confirmed not to exist (NXDOMAIN) will be redirected - not any other error type conditions.
