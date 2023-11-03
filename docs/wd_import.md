---
Slug: import-wizard
Keywords: Import Wizard,Migration
DocID: 68
---
# Import Wizard

The Import Wizard makes it easy to migrate data from another DNS server implementation and/or import zone data from various sources.

You can import [zones](df_zones.md) in four different ways:

- **Import a single zone from another DNS server (zone transfer)**\
Uses a standard [zone transfer](df_zonetransfer.md) to import the zone.\
Security settings on the original server might prevent zone transfers. If this is the case, either adjust the security settings, or use one of the following options instead.

- **Import a single zone from a zone file**\
Import any standard DNS zone file ([RFC1035](http://www.rfc-editor.org/rfc/rfc1035.txt)).\
The zone file can be located on the same computer or in any network shared directory which you have access to.

- **Import a set of zones listed in a DNS server boot/configuration file**\
Import all or some of the zones from another DNS server.\
The import wizard can read 3 different types of boot/configuration file formats:

    - **Standard boot file**\
    This file format is used by earlier versions of Simple DNS Plus, BIND (Unix/Linux DNS server) prior to v. 8.0, and several other DNS servers.\
    This is a simple text file which has one line for each zone, listing authority (primary or secondary), zone name, primary IP address (secondary zones only), and the zone's file name.

    - **Simple DNS Plus v. 5.x "\_zones.sdzdb" file**\
    Proprietary file format used by Simple DNS Plus v. 5.x.

    - **Simple DNS Plus v. 6.0 / 7.x "sdnsplus.db" file**"\
    Simple DNS Plus v. 6.0 / 7.x database file - including backup files.

     - **BIND v. 8.0 or later "named.conf" file**\
    Proprietary file format used by BIND (Unix/Linux DNS server) v. 8.0 and later. This is a text file format structured similar to C programming source code.


    IMPORTANT - Zone files for primary zones must be located in the same directory as the boot/configuration file (zone files are not needed for secondary zones).\
    You may have to copy the files to a different location if they are arranged differently.

 - **Import a list of domains names**\
Creates a new zone for each domain name listed in file copying the data from an existing zone.\
The file that you import from must be a simple plain text file containing a list of domain names. Each line in the file must contain a single domain name and nothing else. You can create such a file for example with Notepad, or with a spreadsheet program such as Excel using the "Save as" function to save in .txt format.
