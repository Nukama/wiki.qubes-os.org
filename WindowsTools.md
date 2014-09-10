---
title: WindowsTools
permalink: /wiki/WindowsTools
---

Qubes Tools for Windows: advanced settings and troubleshooting
==============================================================

Installable components
----------------------

Qubes Tools for Windows (QTW for short) contain several components than can be enabled or disabled during installation:

-   Xen GPL PV drivers (required): drivers for the hardware exposed by Xen.
-   Core Windows Agent: qrexec agent and services. Needed for proper integration with Qubes.
-   Move user profiles: User profiles directory (c:\\Users) will be moved into the private disk backed by private.img. This disk will be initialized/formatted automatically if needed. This feature is useful for Windows-based HVM templates, so child AppVMs can have their separate user profiles.
-   GUI Windows Agent: video driver and gui agent that enable seamless showing of Windows applications on the secure Qubes desktop.
-   Disable UAC: disables User Account Control prompts. *Is this still needed/wanted? Gui agent can handle UAC prompts now.*

It's probably a good idea to install a VNC server in the VM before installing QTW. If something goes very wrong with the Qubes gui agent, a VNC server should still allow access to the OS.

Configuration
-------------

Starting from version 2.2.\* various aspects of Qubes Tools for Windows can be configured through registry. Main configuration key is located in `HKEY_LOCAL_MACHINE\SOFTWARE\Invisible Things Lab\Qubes Tools`. Configuration values set on this level are global to all QTW components. It's possible to override global values with component-specific keys, this is useful mainly for setting log verbosity for troubleshooting. Possible configuration values are:

|**Name**|**Type**|**Description**|**Default value**|
|:-------|:-------|:--------------|:----------------|
|LogDir|String|Directory where logs are created|c:\\Program Files\\Invisible Things Lab\\Qubes OS Windows Tools\\log|
|LogLevel|DWORD|Log verbosity (see below)|2 (INFO)|
|LogRetention|DWORD|Maximum age of log files (in seconds), older logs are automatically deleted|604800 (7 days)|

Possible log levels:

||
|0|Error|Serious errors that most likely cause irrecoverable failures|
|1|Warning|Unexpected but non-fatal events|
|2|Info|Useful information|
|3|Debug|Internal state dumps for troubleshooting|
|4|Verbose|Trace most function calls|

Debug and Verbose levels can generate large volume of logs and are intended for development/troubleshooting only.

To override global settings for a specific component, create a new key under the root key mentioned above and name it as the executable name, without `.exe` extension. For example, to change qrexec-agent's log level to Debug, set it like this:

[![No image "qtw-log-level.png" attached to WindowsTools](/chrome/common/attachment.png "No image "qtw-log-level.png" attached to WindowsTools")](/attachment/wiki/WindowsTools/qtw-log-level.png)

Component-specific settings currently available:

|**Component**|**Setting**|**Type**|**Description**|**Default value**|
|:------------|:----------|:-------|:--------------|:----------------|
|wga|UseDirtyBits|DWORD|Enable experimental feature of the gui agent/qvideo driver: use page table dirty bits to determine changed display regions. This can improve performance but may impact display responsiveness (some changes may not be detected resulting in "stale" image). Needs VM restart to apply change. Gui agent is currently undergoing a significant architectural change and this setting may be removed/not needed in the future.|0|
|wga|DisableCursor|DWORD|Disable cursor in the VM. Useful for integration with Qubes desktop so you don't see two cursors. Can be disabled if you plan to use the VM through a remote desktop connection of some sort. Needs gui agent restart to apply change (locking OS/logoff should be enough since wga is restarted on desktop change).|1|

Troubleshooting
---------------

If the VM is inaccessible (doesn't respond to qrexec commands, gui is not functioning), try to boot it in safe mode:

-   qvm-start --debug vmname
-   mash F8 on the boot screen to enable boot options and select Safe Mode (optionally with networking)

Safe Mode should at least give you access to logs (see above).

If a specific component is malfunctioning, you can increase it's log verbosity as explained above to get more troubleshooting information. Below is a list of components:

||
|qrexec-agent|Responsible for most communication with Qubes (dom0 and other domains), secure clipboard, qrexec services.|
|qrexec-client-vm|Used for communications by the qrexec protocol.|
|wga|Gui agent.|
|QTWHelper|Service that monitors session/desktop changes (logon/logoff/locking/UAC...) and simulates SAS sequence (ctrl-alt-del).|
|prepare-volume|Utility that initializes and formats the disk backed by `private.img` file. It's registered to run on next system boot during QTW setup, if that feature is selected (it can't run *during* the setup because Xen block device drivers are not yet active). It in turn registers move-profiles (see below) to run at early boot.|
|move-profiles|Utility that moves user profiles directory to the private disk. It's registered as an early boot native executable (similar to chkdsk) so it can run before any profile files are opened by some other process. Its log is in a fixed location: `c:\move-profiles.log` (it can't use our common logger library so none of the log settings apply).|


