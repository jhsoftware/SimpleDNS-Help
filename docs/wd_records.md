---
Slug: dns-records-window
Keywords: DNS Records,Records
DocID: 102
---
# DNS Records window

The DNS Records window lists local [zones](df_zones.md) and DNS records in an explorer style window.

The zone list (left) shows all [zones](df_zones.md) currently defined, primary zones with a "P" icon, and secondary zones with an "S" icon.

[Suspended zones](df_suspended.md) are indicated with a red "paused" symbol (two vertical lines) on the icon and a red name.

The record list (right) shows DNS records in the selected zone.

The optional zone folder list (above or to the left of the zone list) can be used to filter the zone list by zone type or zone group.

To edit the properties of an existing zone (left list) or record (right list), simply double click the item (see [Zone Properties](wd_zoneprop.md) and [Record Properties](wd_recprop.md) dialogs).

You can also right-click on a zone, on a record, or in an empty area of either list to quickly access related functions.

To quickly jump to a zone in the list, first click on any zone to ensure that the zone list has focus, then type the first few letters of the zone name. You can do the same in the records pane.

When you have a [reverse zone](df_reverse.md) selected in the zone list, a reverse zone information panel will be available at the bottom of the DNS record list pane.

To easily edit reverse DNS records, click the "Edit IP-to-Name Mappings" button on this panel to open the [Reverse zone IP-to-Name Mappings dialog](wd_iptoname.md).

The following functions are available in the DNS Records window menu:

- **File menu**

    - **New** (also available from the tool bar)

        - **New Zone**\
        Opens the [New Zone Wizard](wd_newzone.md).

        - **New Record [different record types]** (only visible when a primary zone is selected)\
        Open the [Record Properties dialog](wd_recprop.md) to create a new DNS record in the currently selected zone.

        - **New Zone Group**\
        Creates a new zone group in the zone folder pane.

    - **Zone** (also available by right clicking a zone name in the zone list)

        - **Save records** (also available from the tool bar)\
        Saves any changes made to the records of the currently selected zone to disk.

        - **Versions...**\
        View, compare, or restore previous versions of the selected zone. Opens the [Zone versions](wd_zoneversions.md) dialog.

        - **DNSSEC** (only available when primary zone is selected) (also available from the tool bar)

            - **Sign...**\
            DNSSEC sign the selected zone. Opens the [DNSSEC Sign Zone dialog](wd_signzone.md).

            - **Generate DS-records...**\
            Generates DS-record based on the current DNSKEY-records in the selected zone. Opens the [DNSSEC DS-records dialog](wd_ds_recs.md)

            - **Remove...**\
            Removes DNSSEC records (DNSKEY, RRSIG, NSEC, NSEC3, NSEC3PARAM) from the selected zone and disables automatic signing (if enabled).

            - **On-line keys...**\
            Edit the on-line DNSSEC keys for the selected zone. Opens the [DNSSEC Keys dialog](wd_dnsseckeys.md).

            - **Settings...**\
            Update the DNSSEC settings for the selected zone. Opens the [Zone Properties dialog](wd_zoneprop.md) / DNSSEC tab. 


        - **Suspend / Resume**\
        Suspends a zone, or resumes as [suspended zone](df_suspended.md).

        - **Reload from Primary**\
        Forces the currently selected secondary zone to be [zone transferred](df_zonetransfer.md) from the primary DNS server.

        - **Make Copy**\
        Make a copy of the currently selected zone.

        - **Move to Group** (only available when the zone folders list is visible - see View menu below)\
        Moves the currently selected zone to a different zone group.\
        NOTE: You can also move a zone to a different group simply by dragging it with the mouse.

        - **Delete** (also available from the tool bar)\
        Delete the currently selected zone.


        - **View/Save as standard zone file**\
        See what a standard zone file would look like for the selected zone. Opens the [Standard zone file dialog](wd_zoneraw.md).

        - **Properties** (also available from the tool bar)\
        View/edit the properties of the currently selected zone or record.

    - **Zone Group** (only available when the zone folders list is visible - see View menu below)

        - **Rename**\
        Renames the currently selected zone group.

        - **Delete**\
        Delete the currently selected zone group and all the zones in it.

    - **Import**\
    Opens the [Import Wizard](wd_import.md).

    - **Export**\
    Opens the [Export Wizard](wd_exportwiz.md).

    - **Connect to Remote**\
    Opens a new instance of the DNS Records module connecting to an instance of Simple DNS Plus running on a remote computer.\
    NOTE: Remote Management must be enabled in the [Options dialog / Remote Management section](wd_opt_remote.md) on the remote Simple DNS Plus instance.

    - **Exit**\
    Closes the DNS Records window.

- **Edit menu**

    - **Cut**\
    Copies the currently selected DNS records to the clipboard and removes them from the currently selected zone.

    - **Copy**\
    Copies the currently selected DNS records to the clipboard.

    - **Paste**\
    Pastes previously copied DNS records from the clipboard to the currently selected zone.

    - **Paste As**\
    Pastes previously copied DNS records from the clipboard to the currently selected zone using a different record name.

    - **Delete**\
    Removes the currently selected zone or DNS records - depending on which list (zone or record) has focus.

    - **Select All**\
    Selects all DNS records in the currently selected zone.

    - **Invert Selection**\
    Inverts the current selection of DNS records.

    - **Properties**\
    Opens the [Zone Properties dialog](wd_zoneprop.md) or the [Record Properties dialog](wd_recprop.md) for the currently selected item depending which list (zone or record) has focus.

    - **Set TTL**\
    Updates the [TTL](df_ttl.md) value of the currently selected DNS records.

- **View menu**

    - **Zone Folders**\
    Select where the zone folders list should be displayed in relation to the zone list pane.

    - **Sort Records By**\
    Select which column and in which order the DNS record list should be sorted.\
    NOTE: You can also sort the DNS records by clicking on the DNS record list column headers.

    - **IDN native characters**\
    Enables/disables display of native characters for [IDNs](df_idn.md).

    - **DNSSEC records**\
    Show / hide [DNSSEC](df_dnssec.md) records (DNSKEY, RRSIG, NSEC, NSEC3, NSEC3OPTIONS) in the record list.

    - **Toolbar**\
    Display / hide the toolbar.

    - **Status Bar**\
    Display / hide the status bar at the bottom of the window.

    - **Refresh**\
    Reloads the currently selected zone (in case it was updated by another process).

- **Tools menu**

    - **Find Zone**\
    Quickly locate a zone in the zone list.\
    NOTE: This function only searches zones currently in the zone list. To search all zones makes sure to select "All zones" in the zone folders list (if displayed).

    - **Find Next Zone**\
    Repeats the last "Find Zone" starting at the current selection in the zone list.

    - **Quick Zone Wizard** (also available from the tool bar)\
    Opens the [Quick Zone Wizard](wd_quickdom.md)

    - **Bulk Update Wizard** (also available from the tool bar)\
    Opens the [Bulk Update Wizard](wd_bulkwiz.md).

    - **Check Internet Delegations**\
    Opens the [Check Internet Delegations](wd_chkdeleg.md) wizard.

    - **Count Zones**\
    Displays the total number of zones, primary zones, primary forward zones, primary reverse zones, secondary zones, and number of zones in the currently selected zone group (if any).

    - **Default Zone Values**\
    Opens the [Default Zone Values dialog](wd_defzoneval.md).

- **Help menu**

    - **Contents \& Index** (also available from the tool bar)\
    Display this help file.

    - **Online support**\
    Open the online support page in your browser.
