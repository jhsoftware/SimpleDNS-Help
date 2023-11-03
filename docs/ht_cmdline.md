---
Slug: how-to-use-command-line-options
Keywords: Command line options,DOS prompt
DocID: 19
---
# How to use command line options

When Simple DNS Plus is running, you can use the following command line (DOS prompt) options:

(Make sure you run these from the directory where Simple DNS Plus is installed)

### Backup

    sdnsplus.exe -b <to-file>

Makes a backup of the live SQLite database used by Simple DNS Plus.

Can be used in scripts and schedulers to automate backups.

### Clear cache

    sdnsplus.exe -c

Removes all records from the cache.

Same as selecting "Clear Cache" from the [main window](wd_mainscreen.md) / File menu.

### Set remote password

    sdnsplus.exe -m <password>

Enables remote management and sets the remote management password (see [Options / Remote Management section](wd_opt_remote.md)).

This can be used to gain remote access to Simple DNS Plus - for example on a Server Core machine - see <https://simpledns.plus/kb/119>.


### Start service

    sdnsplus.exe -ss

Starts the Simple DNS Plus service (requires "run as administrator").


### Shutdown

    sdnsplus.exe -x

Shutdown Simple DNS Plus.


### Load/re-load/update zone (DEPRECATED)

    sdnsplus.exe -z  z:<zone-name> [f:<file-name>] [p:<primary-ip>] [g:<group-id>]

Loads, re-loads, and/or updates the status of a specific [zone](df_zones.md).

The f:file-name parameter is only required if this is a new zone. Specify the full path to the file, and make sure to use quotes if the path contains spaces ("f:C:\my dns data\...")

The p:primary-ip parameter is only required if this is a secondary zone.

The g:group-id is optional and refers to the numerical zone group ID.

This option is deprecated and is available for backwards compatibility only. It will eventually be removed.\
Use [HTTP API](ht_http.md) functions instead.
Note that the HTTP API can also be accessed from the command line or through batch scripting - for example using cURL (<https://curl.haxx.se>).


### Unload/remove zone (DEPRECATED)

    sdnsplus.exe -u  <zone-name>

Unloads / removes a [zone](df_zones.md).

This option is deprecated and is available for backwards compatibility only. It will eventually be removed.\
Use [HTTP API](ht_http.md) functions instead.
Note that the HTTP API can also be accessed from the command line or through batch scripting - for example using cURL (<https://curl.haxx.se>).


### Run server in command line mode

    sdnsmain.exe -c

Run Simple DNS Plus in command line mode (no UI / logs directly to console).

Note: This mode is meant for testing / diagnostics purposes only. Not for continuous daily operation.

While running in command line mode, you can use press following keys:

- **P** - Pause/resume the server.
- **S** - Provide simple statistics (like the UI status bar).
- **C** - Clear the cache.

To shut down the server, press CTRL+C.
