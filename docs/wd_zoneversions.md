---
Slug: zone-versions-dialog
DocID: 109
---
# Zone versions dialog

Use this dialog to view, compare, or restore old versions of a zone.

Select a version of the zone (by serial number) in the left list to see the records of that version, or select two versions to compare them (hold down CTRL key while clicking versions).

With a single version selected, click the "Restore" button to restore that version, or click the "View/Save as standard zone file..." to export it (open the [Standard zone file dialog](wd_zoneraw.md) for the selected version).

Each time you save a zone, or other updates are made to the zone (such as dynamic updates), a new version (with a new SOA-record serial number) is created.

You can specify the number of versions to retain in the Options dialog, DNS / Local Zones / [Zone Versions section](wd_opt_zoneversions.md).
