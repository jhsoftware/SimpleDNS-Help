---
Slug: definition-tsig
DocID: 14
---
# Definition - TSIG

Simple DNS Plus supports TSIG signed [zone transfers](df_zonetransfer.md) and [dynamic updates](df_dyndns.md).

TSIG ( is an extension to the DNS protocol where a cryptographic signature is added to DNS packets.

This is used to ensure that DNS packets originate from an authorized sender, and that they have not been tampered with along the way.

Both request and response packets are signed by the sender and verified by the receiver.

In order to exchange TSIG signed DNS packets the client and server must both know and use the same TSIG key. A response to a signed request is always signed with the same key as the request.

A TSIG key consists of a key name, a signing algorithm, and a secret:

 - **Key name**

    Similar to a login user ID.

    The key name must be specified in domain name format, but can otherwise be anything you wish.

    RFC2845 recommends to use a name which identifies both the client and the server, for example, "client.domain1.server.domain2".

    However, it does not have to be part of, or related to, any real domain name. It works just as fine, and is probably easier, using just a simple name like "robert".

 - **Signing algorithm**

    Simple DNS Plus supports HMAC-MD5, HMAC-SHA1, HMAC-SHA256, HMAC-SHA384, and HMAC-SHA512.

    HMAC-MD5 is the most widely supported algorithm but is considered outdated and less secure than the SHA based algorithms.

    If some software (including earlier versions of Simple DNS Plus) supports TSIG signatures but does not allow you to specify an algorithm, this typically means that it only supports HMAC-MD5 (originally the only defined option).

    HMAC-MD5 uses a 128 bit signature, HMAC-SHA1 uses a 160 bit signature, and the other HMAC-SHA algorithms use a signature with a bit length equal to the number in the algorithm name.

    While algorithms with longer signatures are more secure, they also take up more space in DNS packets, which limits the size of actual DNS data that can fit in a response packet sent over UDP. For incremental zones transfers, this directly affects how often the servers are forced to switch to slower TCP operations for synchronization.

 - **Secret**

    A base 64 encoded binary value. Similar to a login password.

    In the Simple DNS Plus user interface, you can click a "Generate" button to create a random or pass phrase based value.

    Using a pass phrase based value makes it easier to copy the key to a client application or another server which has the same function, but it also potentially makes the secret easier to guess.

> [!YELLOW] **Important**
>
> To prevent "replay attacks" TSIG signatures are time stamped and only valid within a short time window (usually +/- 5 minutes). It is therefore critical that both client and server have the correct time. This is best achieved using automatic periodic time synchronization against an Internet time server - which is enabled by default on newer Windows versions, but may require special configuration or software on older Windows versions and other operating systems.\
> Also make sure that the correct time zone is configured on both computers since the TSIG time stamp is based on UTC time (= local time +/- time zone).

TSIG is defined in [RFC2845.](http://www.rfc-editor.org/rfc/rfc2845.txt)
