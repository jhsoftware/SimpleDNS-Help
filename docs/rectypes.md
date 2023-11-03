---
Slug: dns-record-types
DocID: 29
---
# DNS Record types

## Commonly used record types

- [A](rec_a.md) (Host address)
- [AAAA](rec_aaaa.md) (IPv6 host address)
- [ALIAS](rec_alias.md) (Auto resolved alias)
- [CNAME](rec_cname.md) (Canonical name for an alias)
- [MX](rec_mx.md) (Mail eXchange)
- [NS](rec_ns.md) (Name Server)
- [PTR](rec_ptr.md) (Pointer)
- [SOA](rec_soa.md) (Start Of Authority)
- [SRV](rec_srv.md) (location of service)
- [TXT](rec_txt.md) (Descriptive text)

To setup one of these records, right-click a zone in the left list in the DNS Records window, and select the "New ...-record" from the pop-up menu.

## Records types used for DNSSEC

- [DNSKEY](rec_dnskey.md) (DNSSEC public key)
- [DS](rec_ds.md) (Delegation Signer)
- [NSEC](rec_nsec.md) (Next Secure)
- [NSEC3](rec_nsec3.md) (Next Secure v. 3)
- [NSEC3PARAM](rec_nsec3param.md) (NSEC3 Parameters)
- [RRSIG](rec_rrsig.md) (RRset Signature)

To setup one of these records, use the [DNSSEC Sign Zone](wd_signzone.md) function.

## Less commonly used record types:

- [AFSDB](rec_afsdb.md) (AFS Data Base location)
- [CAA](rec_caa.md) (Certification Authority Authorization)
- [CERT](rec_cert.md) (Certificate / CRL)
- [DHCID](rec_dhcid.md) (DHCP Information)
- [DNAME](rec_dname.md) (Non-Terminal DNS Name Redirection)
- [HINFO](rec_hinfo.md) (Host information)
- [HTTPS](rec_https.md) (HTTPS Service binding and parameter specification)
- [LOC](rec_loc.md) (Location information)
- [NAPTR](rec_naptr.md) (Naming Authority Pointer)
- [RP](rec_rp.md) (Responsible person)
- [TLSA](rec_tlsa.md) (Transport Layer Security Authentication)

To setup one of these records, right-click a zone in the left list in the DNS Records window, and select "Other new record" from the pop-up menu.
