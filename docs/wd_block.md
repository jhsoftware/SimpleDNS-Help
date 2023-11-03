---
Slug: ip-address-blocking-dialog
Keywords: IP Address Blocking,Blocking
DocID: 59
---
# IP Address Blocking dialog

Someone sending an extreme number of DNS requests in rapid succession may be a hacker trying to crash the server or prevent others from using the service.

You can use the functions in this dialog to automatically or manually block such hackers or IP addresses which for any reason run amok sending you DNS requests.

Please note that this feature does not block network traffic other than DNS requests - to block any other type traffic use a firewall.

If you enable automatic blocking, make sure to add any local computers and servers that you know may send a lot of DNS requests on the "Trusted IP Addresses" first.

Especially e-mail servers may send a lot of DNS requests to check the validity of incoming e-mails.

The "IP Address Blocking" dialog has 3 tabs:

- **Auto Blocking**

    - **Automatically block IP addresses which send too many DNS requests too quickly (DoS attack)**\
        Use to enable/disable automatic blocking

    - **Max. number of DNS requests**\
        When an IP address sends more than this number of DNS requests within the time specified, it will be automatically be blocked and further requests from this IP address are ignored.\
        Setting a higher number for 'within seconds' allows for larger spikes in traffic, while still blocking sustained high request rates.
        A typical workstation computer should not send more than 10-25 requests per second, but we recommend you set this value to at least 30 (f.x. 150 within 5 seconds) so that no legitimate clients get blocked.

    - **Block**\
        Specify for how long automatic blocks should last (when/if the automatically added IP blocking should expire).

- **Blocked IP Addresses**\
    List of IP addresses currently blocked. You can add, edit, and remove entries.\
    When you add or edit an entry you can specify the IP address (single, range, or subnet) to block, for how long, and comments (these comments show up in the log when a request is blocked).\
    To quickly remove multiple items from the list, you can hold down the Shift or Ctrl keys while selecting items and then click the "Remove" button.

- **Trusted IP Addresses**\
    List of IP addresses are trusted and will not be blocked automatically. You can add, edit, and remove entries.\
    When you add or edit an entry you can specify the IP address (single, range, or subnet) to trust, for how long, and comments.\
    To quickly remove multiple items from the list, you can hold down the Shift or Ctrl keys while selecting items and then click the "Remove" button.

See also: [How to secure your server](ht_secure.md)
