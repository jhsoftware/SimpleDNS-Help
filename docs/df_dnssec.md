---
Slug: definition-dnssec
DocID: 3
---
# Definition - DNSSEC

Similar to digital signatures for e-mail, DNSSEC authenticates that DNS records originate from an authorized sender (DNS server) using private/public key cryptography.

The main purpose of this is to protect DNS against falsified information ([DNS spoofing](ht_secure.md#spoofing)).

DNSSEC does NOT encrypt or hide anything - all data is still in "clear text". Its only purpose is verification of data authenticity.

### Concepts

-   **DNSSEC signing**

    When a [zone](df_zones.md) is DNSSEC signed, a number of DNS records are added to the zone (indeed DNSSEC signing a zone can make it many times larger).
    
    First a [DNSKEY-record](rec_dnskey.md) is added for each key used to sign the zone.
    DNSKEY-records hold the public keys that clients can use the verify signatures.
    
    Next, an [NSEC-record](rec_nsec.md) or [NSEC3-record](rec_nsec3.md) is added for each unique record name in the zone (+ a single [NSEC3PARAM-record](rec_nsec3param.md) if using NSEC3).
    Each NSEC/NSEC3 record lists all the record types that exist for the name that it represents, and points to the next record name in the zone forming a chain between all existing names in the zone.
    These (signed) NSEC/NSEC3 records are returned in responses to DNSSEC enabled queries (DO flag set) for non-existing names/types, so that clients can verify the non-existence.
    
    Finally, all the DNS records in the zone (including the DNSKEY and NSEC/NSEC3 records) are signed by adding an [RRSIG-record](rec_rrsig.md) for every unique record name and type combination in the zone. RRSIG-records for the records they sign are returned in responses to DNSSEC enabled queries.

- **Delegation / link of trust**

    There are no 3rd party certification authorities involved with DNSSEC - you create your own keys (or private/public key sets) - see [DNSSEC Keys dialog](wd_dnsseckeys.md).
    
    In order to establish a "link of trust" so that other Internet users can verify your keys and signatures, you create a [DS-record](rec_ds.md) (delegation signature) containing a cryptographic hash of one of your KSK (see key types below) DNSKEY-records
    (see "DS Records" button in the [DNSSEC Keys dialog](wd_dnsseckeys.md)).

    This DS-record needs to be included (and signed) in the parent zone. For example if your domain name is "example.se", the DS-record needs to be added to the ".se" zone. The procedure for "uploading" the DS-record depends on your parent zone / TLD operator, and/or your domain name registrar.

    Note that some registrars will automatically generate the DS-record(s) for you based on the DNSKEY-records in your zone.

    TLD level domains (".se" etc.) are "linked" to the root zone the same way. And this way all DNSSEC signed zones are linked up to the root.\
    DNSSEC enabled resolvers are configured with a copy of the public key part of the key signing the root - and are therefore able to verify any correctly signed / delegated DNS zone on the Internet.

    
- **Key types - KSK / ZSK / Simple**

    [RFC4641](http://www.rfc-editor.org/rfc/rfc4641.txt) (DNSSEC Operational Practices) defines two key types; "Key Signing Key" (KSK) and "Zone Signing Key" (ZSK).
    
    Typically a zone is signed with both a KSK and a ZSK (or two of either type during rollovers - see below).
    
    A KSK only signs the public key records (DNSKEY) for a zone.
    KSKs are used as "Secure Entry Points" (SEP), and are referenced in parents zones through a DS-record (see above).
    
    A ZSK signs all the other records in a zone.
    ZSKs are not Secure Entry Points, and are not referenced directly in parent zones (but indirectly because the DNSKEY-record representing the ZSK is signed by the KSK).
    
    A KSK is often a stronger key (algorithm / key size) than a ZSK.
    
    This KSK/ZSK arrangement allows a zone operator to change his ZSKs (see Rollover below) without having to update the delegation signature in the parent zone. And it makes it possible to re-sign a zone as needed using only the ZSK. The KSK is only needed when changing keys (because this only signs the DNSKEY records - which only change when the keys change), allowing the KSK to be stored in a more secure manner.
    
    Simple DNS Plus also supports a 3rd key type - "Simple".
    This is basically a combined KSK and ZSK - a key used as a Secure Entry Point and also to sign ALL records in a zone.
    This is just a simpler model which may be easier to use in some scenarios - but of course doesn't provide the benefits of KSK/ZSK separation.


- **Key rollover**

    A "rollover" is the process of replacing a DNSSEC key - adding a new key and removing the old - along with the related DNS records. 
    
    It is recommended (in RFCs and by various security experts) that DNSSEC keys are replaced periodically.
    Generally KSKs should be replaced every few years and ZSKs every few months.
    
    During a rollover, DNSSEC records for both the old and the new key should be present in the zone for a short period allowing old keys to time out in caches etc. 
    
    This means that in the overlapping periods, a zone might be signed by up to 4 different keys (2 KSKs + 2 ZSKs) at the same time.

- **Signature validity period / expiration**

    When you sign a zone, you specify how long the signatures are valid for. This stores a fixed expiration date/time as part of each signature record (RRSIG).
    
    A zone must always be re-signed before the previous signatures expire.
    
    This validity period should be kept as short as possible, so that any bad data will time out as quickly as possible - but:
    
    - If you are using automatic signing (see below), the validity period should be long enough to allow for an outage on the primary DNS server (which does the signing) to be recovered before the signatures expire. Secondary servers do NOT automatically re-sign the zone while the primary is out.

    - If you are not using automatic signing, then the validity period also depends on how often you are willing to manually re-sign the zone.
    
### DNSSEC in Simple DNS Plus{#sdns}

Simple DNS Plus can DNSSEC sign zones, host these DNSSEC signed zones and respond to DNSSEC enabled queries for these zones, and it can automate some of the processes around this (signing zones and updating keys).

However Simple DNS Plus does not request or validate DNSSEC signatures while resolving other Internet domain names. We may add this in a future version, but for now DNSSEC support in Simple DNS Plus is about hosting - not resolving.

- **DNSSEC signing**

    In Simple DNS Plus, zones can be DNSSEC signed 3 different ways:

    1) On demand, through the GUI.\
    See the [DNSSEC Sign Zone dialog](wd_signzone.md))
    
    2) Via the [HTTP API](ht_http.md).\
    `POST /zones/{zonename}/dnssecsign`
    
    3) Automatically - whenever records in the zone are updated - or a specified number of days pass.\
    This works with any kind of record update - including GUI, Bulk Update Wizard, HTTP API (v. 1 and 2), command line, dynamic DNS updates, updates from plug-ins, etc.\
    This is configured in the DNSSEC tab of the [Zone Properties dialog](wd_zoneprop.md).
    
    Signing happens in one of two modes depending on the keys used - either:

    1) *Full signing*: If there is one or more KSKs or Simple keys, then ALL existing DNSSEC records will be removed and then re-created.
    2) *ZSK only signing*: If there are no KSKs or Simple keys (all keys are ZSKs), then the existing DNSKEY-records and RRSIG-records signing those DNSKEY-records, will be left alone. The rest of the DNSSEC records will be removed and then re-created.

    
    DNSSEC signing a zone is a CPU intensive operation, so we have programmed it so that this always happens on a separate CPU thread. This way it should not interfere much with the general performance of Simple DNS Plus - as long as you have at least two CPU cores. Of course most computers today have this, but this might be something to consider if you run Simple DNS Plus on a virtual machine.

- **Automatic ZSK rollover / key deletion**

    As part of the automatic DNSSEC signing, Simple DNS Plus can also do automatic ZSK rollovers (periodically add a new ZSK and remove the old) - see the DNSSEC tab of the [Zone Properties dialog](wd_zoneprop.md).
    
    On-line keys can also be scheduled for automatic deletion. See the [DNSSEC key dialog](wd_dnsseckey.md).\
    This is useful for example if you are doing a KSK rollover. You simply add the new KSK and schedule the old KSK to be deleted 2 weeks later. This way you don't have to touch this again until the next KSK rollover.

- **Key storage - on-line / off-line**

    DNSSEC keys for use by Simple DNS Plus can be stored either "on-line" or "off-line":
    
    - "On-line" means that the keys are stored in the Simple DNS Plus database along with zone data.

    - "Off-line" means that the keys are stored in a separate DNSSEC key file - ideally physically stored separate from the server when not in use.
    Off-line keys can only be used when signing zones "on demand" through the GUI - not when zones are signed automatically or via the HTTP API.
    
    On-line keys can be exported to a DNSSEC key file (compatible with older versions of Simple DNS Plus), and off-line keys in a DNSSEC key file can be imported. These export/import functions can also be used to move on-line keys between Simple DNS Plus servers. See [DNSSEC Keys dialog](wd_dnsseckeys.md).
    
    Storing DNSSEC keys on-line is convenient, but is also less secure than if the keys were stored off-line away from the server. Of course, it is not possible to do automatic signing without keys being available on-line.
    
    As a compromise, it is possible to use a combination of on-line and off-line keys:
    
    With a KSK/ZSK setup, the KSKs are only needed whenever keys are added or removed (to sign the DNSKEY records). By storing KSKs off-line (in a key file) and ZSKs on-line, Simple DNS Plus can still automatically sign the zone whenever records are updated. And you only need to get out the key file with the KSKs when doing key maintenance. This setup allows for storing KSKs away from the server - for example on an encrypted USB drive.
    
    This does however prevent automatic ZSK rollover and automatic scheduled key deletion (not possible without on-line KSKs).

### A note about dynamic DNS data / ALIAS records{#dyndata}

Several [options](wd_options.md) in Simple DNS Plus provide dynamic and/or synthesized DNS records, which will NOT automatically be DNSSEC signed. So make sure not to use those options in any way that would result in serving un-signed records under a domain that should be signed.

This includes [ALIAS records](rec_alias.md) - which is also a way to synthesize records. Such records cannot be DNSSEC signed.
    
### HTTP API commands for DNSSEC

It is also possible to DNSSEC sign zones and manage DNSSEC keys (on-line keys only) through the [HTTP API](ht_http.md):

- To DNSSEC sign a zone using the on-line DNSSEC keys (for zones NOT configured to sign automatically):\
  `POST /zones/{zonename}/dnssecsign`
- To retrieve a list of on-line DNSSEC keys for a zone:\
  `GET /zones/{zonename}/dnsseckeys`
- To retrieve a specific on-line DNSSEC key:\
  `GET /zones/{zonename}/dnsseckeys/{keyid}`
- To create a new or update an existing on-line DNSSEC key:\
  `PUT /zones/{zonename}/dnsseckeys/{keyid}`
- To delete an on-line DNSSEC key:\
  `DELETE /zones/{zonename}/dnsseckeys/{keyid}`
- To generate a list of DS-records (for inclusion in parent zone) based on the DNSKEY-records in the zone:\
  `GET /zones/{zonename}/dnssecds`
- To retrieve / update the settings for a zone - including the DNSSEC and auto signing settings:\
  `GET/PUT /zones/{zonename}`
  
Note that the DNSSEC key information provided through the HTTP API does NOT include the private cryptographic key data of the DNSSEC keys - only meta data about them.

## RFCs{#rfc}

DNSSEC is defined in [RFC3225](http://www.rfc-editor.org/rfc/rfc3225.txt), [RFC4033](http://www.rfc-editor.org/rfc/rfc4033.txt), [RFC4034](http://www.rfc-editor.org/rfc/rfc4034.txt), [RFC4035](http://www.rfc-editor.org/rfc/rfc4035.txt), [RFC4641](http://www.rfc-editor.org/rfc/rfc4641.txt), and [RFC5155](http://www.rfc-editor.org/rfc/rfc5155.txt).
