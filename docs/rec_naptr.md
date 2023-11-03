---
Slug: naptr-records
Keywords: NAPTR record type,Naming Authority Pointer
DocID: 45
---
# NAPTR-Records (Naming Authority Pointer)

NAPTR-records are used to store rules used by DDDS (Dynamic Delegation Discovery System) applications.

One example is "ENUM" which allows an end user to type a telephone number into e.g. a web browser and access a listing of Internet resources (URI) for that number, such as addresses for IP telephony, e-mail or web sites.

For more information on "ENUM", see <http://www.ripe.net/enum> or <http://enum.nic.at>

See also [ENUM - Mapping telephone numbers to SIP or e-mail addresses in DNS](https://simpledns.plus/kb/42)

The "Order" field is a number (0 to 65535) specifying the order in which multiple NAPTR records must be processed (low to high) by the application.

The "Preference" field is equivalent to the Priority value in the DDDS algorithm. It is a number (0-65535) that specifies the order (low to high) in which NAPTR records with equal Order values should be processed.

The "Flags" field contains flags to control aspects of the rewriting and interpretation of the fields in the record. Flags are single characters from the set A-Z and 0-9. The use of this field is specified by the individual DDDS application.

The "Services" field specifies the service parameters applicable to this delegation path. The individual DDDS application specifies the possible values for this field.

The "Reg. Exp." field contains a substitution expression that is applied to the original string held by the client in order to construct the next domain name to lookup. See the DDDS algorithm specification for the syntax of this field.

The "Replacement" field specifies the next domain name (fully qualified) to query for depending on the potential values found in the flags field. This field is used when the regular expression is empty (a simple replacement operation). The "Reg.Exp." and "Replacement" fields are mutually exclusive (only one can contain a value).

To create a new NAPTR-record, right-click a zone in the left list in the [DNS Records window](wd_records.md), and select "Other new record" from the pop-up menu.

This record type is defined in [RFC3403](http://www.rfc-editor.org/rfc/rfc3403.txt).
