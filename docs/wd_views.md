---
Slug: main-window-views
Keywords: Views,Performace Graph,Active Log View,Plug-in View
DocID: 106
---
# Main window - Views

The center of the [Main window](wd_mainscreen.md) can host different "views".

Use the View menu to open new Views.

You can have multiple views open at the same time.

Initially all open views will be in the same "tab group", and you can switch between views by clicking on the tabs.

To make two or more views visible at the same time, you can open additional tab groups either using the Windows menu, or by mouse-dragging a tab towards the center of the view and releasing it on the "docking diamond" when the desired position is indicated.

When multiple tab groups are visible, you can resize them with the mouse by dragging the splitter bars between the tab groups.

## Performance Graph View

Shows a graph of the number of requests received per second during the last minute.

## Active Log View

Shows current log activity.

See [How to read the log](ht_readlog.md).

The level of detail and number of lines displayed can be customized through the [Options dialog / Logging / Log Details section](wd_opt_logdet.md).

If the log windows is scrolling too fast, you can pause it using the "Pause Active Log" function from the View menu, or from the right-click menu, or press F9.

If you need to copy text from the log, use the "Active Log Snapshot" function from the Tools menu, or from the right-click menu, or press CTRL+F9.

You can also clear the window using the "Clear" function from the right-click menu.

Please note that the Active Log uses considerable CPU time due to the volume of data that must be converted into clear text. On a busy server we recommend closing this View when not needed.

## Plug-in Views

Some plug-ins also have "views", for example, the DHCP Server [plug-in](pi_overview.md).

A separate view will be available for each such plug-in instance configured in the [Plug-Ins instances dialog](wd_plugins.md).
