---
Slug: plug-in-instances-dialog
Keywords: Plug-Ins instances
DocID: 100
---
# Plug-In Instances dialog

- **Plug-In instances and query order**

    List of plug-in instances, and their relative query order.
    A permanent "[LOCAL DNS ZONES]" item in the list indicates the query order of plug-ins relative to local DNS zones.

    To add a new plug-in instance, click the "Add..." button.

    To configure an existing plug-in instance, select it in the list and click the "Properties" button. This will open the [plug-in instance dialog](wd_plugininst.md).

    To remove a plug-in instance, select it in the list and click the "Remove" button.

    Plug-in instances are queried in the order listed. To change the order, select a plug-in instance or [LOCAL DNS ZONES] in the list and click the "Up" or "Down" buttons.

    Use the "Export" and "Import" buttons to copy plug-in instance configuration between Simple DNS Plus instances.\
    Clicking the "Export" button will copy the configuration of the selected plug-in instance to the Windows clipboard (JSON format), you can then Remote Desktop into the other Simple DNS Plus server, and click the "Import" button there, and a new plug-in instance will be created there with the same settings.


See also: [Plug-Ins Overview](pi_overview.md)
