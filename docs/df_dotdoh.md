---
Slug: definition-dot-doh
DocID: 4
---
# Definitions - DNS over TLS (DoT) / DNS over HTTPS (DoH)

Standard DNS queries (UDP/TCP) are sent in plain text, which means anyone "listening" to the network can read them. This is a privacy issue, especially on the first leg between the user device and the resolving DNS server (think coffee shop wifi hotspot).

DNS over TLS (DoT) / DNS over HTTPS (DoH) encrypt DNS queries and responses - to keep user data private and secure.

DNS over TLS (DoT) and DNS over HTTPS (DoH) use the same type of encryption - TLS.
The difference is that DNS over HTTPS (DoH) uses an additional network layer (HTTP). This makes network packets a bit larger (the HTTP headers), but since it is standard HTTPS and use the standard HTTPS port (443), network packets are indistinguishable from regular HTTPS traffic (making censorship harder) - and it can use standard HTTP tools and services (like reverse proxy servers).
With DNS over TLS (DoT), network packets are smaller, but you need to open another port (853) making network packets easier to categorize, and it cannot use standard HTTP tools and services.

### Operating system support

- **Windows 11** and **Windows Server 2022** support DoH.\
See how to enable: [Windows 11](https://simpledns.plus/kb/199) / [Windows Server 2022](https://simpledns.plus/kb/200).

- **MacOS** 11+ (BigSur) and **IOS** 14+ support both DoH and DoT.\
See how to enable: [MacOS](https://simpledns.plus/kb/201) / [IOS](https://simpledns.plus/kb/202).

- **Android** v. 9+ supports DoT.\
See how to enable: [Android](https://simpledns.plus/kb/198)

- **Chrome OS** does not support DoT or DoH at the operating system level, but the Chrome browser running on Chrome OS supports DoH (see below).

### Browser support

Some modern browsers support DoH independently of the operating system (also works on earlier versions of Windows).

See how to enable: [Chrome](https://simpledns.plus/kb/195) / [Firefox](https://simpledns.plus/kb/197) / [Edge](https://simpledns.plus/kb/196).

Note: Safari (on MacOS and IOS) does not have such a setting, but DoT/DoH can be enabled in these operating systems (see above).
