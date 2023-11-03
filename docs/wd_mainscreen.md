---
Slug: main-window
Keywords: Main window
DocID: 72
---
# Main window

The main window consists of a [Menu](#menu), a [Toolbar](#toolbar), a [Status Bar](#statusbar), and different optional [Views](wd_views.md).

## Menu{#menu}

- **File Menu**

    - **Pause / Start server**\
    Used to pause and re-start serving DNS requests.

    - **Edit DNS Records**\
    Opens the [DNS Records](wd_records.md) window.

    - **Clear DNS Cache**\
    Unloads all [cached](df_cache.md) records.\
    Use if you suspect that invalid cached data is causing problem.\
    Can also be useful, for example, if you want to see how a domain name is resolved from the root up.

    - **Connect to Remote...**\
    Starts a new instance of the Simple DNS Plus user interface for an instance running on a remote computer.\
    NOTE: Remote Management must be enabled in the [Options dialog / Remote Management section](wd_opt_remote.md) on the remote Simple DNS Plus instance.

    - **Shutdown Simple DNS Plus**\
    Shuts down the Simple DNS Plus service and user interface.

- **View Menu**

    - **Toolbar**\
    Toggles the [Toolbar](wd_mainscreen.md#toolbar) on / off.

    -  **Status Bar**\
    Toggles the [Status Bar](wd_mainscreen.md#statusbar) on / off.

    - **Pause Active Log**\
    Pauses the log display in the Active Log [View](wd_views.md).

    - **Performance Graph**\
    Shows the Performance Graph [View](wd_views.md).

    - **Active Log**\
    Shows the Active Log [View](wd_views.md).

    - **[Plug-In Views]**\
    Different [plug-ins](pi_overview.md) such as the DHCP Server plug-in have their own [View](wd_views.md)

- **Tools Menu**

    - **Plug-Ins...**\
    Opens the [Plug-Ins instances](wd_plugins.md) window.

    - **DNS Look Up...**\
    Opens the [DNS Look Up](wd_lookup.md) tool window.

    - **DNS Cache Snapshot...**\
    Opens the [Cache Snapshot Viewer](wd_snapshot.md) window.

    - **Active Log Snapshot...**\
    Use this function if the [Active Log View](wd_views.md) is scrolling to fast or you need to copy text from the log.

    - **IP Address Blocking...**\
    Opens the [IP Address Blocking](wd_block.md) dialog.

    - **Options**\
    Opens the [Options](wd_options.md) dialog.

- **Window Menu**

    - **New Horizontal / Vertical Tab Group**\
    Splits the display into two tab groups. Only available when other [Views](wd_views.md) are grouped with the selected View.

    - **Tile Horizontally / Vertically**\
    Quickly organize the currently open [Views](wd_views.md).

    - **Reset Window Layout**\
    Move all open [Views](wd_views.md) into a single tab group.

- **Help Menu**

    - **Contents \& Index**\
    Opens this help file

    - **Online Support**\
    Opens the Simple DNS Plus support web page in your default browser.

    - **Check for Updates**\
    Checks if you are running the most recent version of Simple DNS Plus.

    - **Activate Product**\
    Select this function when you have purchased a Simple DNS Plus license (at <https://simpledns.plus/buy>) to enter your license key. This will remove the evaluation time restriction.

    - **Support File**\
    Generates a file containing various information about your system and the state of Simple DNS Plus which can be helpful for trouble shooting by JH Software support staff.

    - **About Simple DNS Plus**\
    Displays the Simple DNS Plus version number and license status.



## Toolbar{#toolbar}

- **Options button**\
    Opens the [Options](wd_options.md) dialog.

- **Records button**\
    Opens the [DNS Records](wd_records.md) dialog.

- **Plug-Ins button**\
    Opens the [Plug-Ins instances](wd_plugins.md) window.

- **Look Up button**\
    Opens the [DNS Look Up](wd_lookup.md) tool.

- **Cache button**\
    Opens the [Cache Snapshot Viewer](wd_snapshot.md).

- **Help button**\
    Opens this help file.



## Status Bar{#statusbar}

The Status Bar consists of three sections:

- **Status**\
    Show current server status - and if running, the total up-time.

- **Requests**\
    Total number of DNS requests received.

- **Cache**\
    Number of DNS records currently in the cache.
