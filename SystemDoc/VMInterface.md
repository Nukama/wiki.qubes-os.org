---
title: VMInterface
permalink: /wiki/SystemDoc/VMInterface
---

VM Configuration Interface
==========================

Qubes VM have some settings set by dom0 based on VM settings. There are multiple configuration channels, which includes:

-   XenStore
-   QubesDB - replacing most of xenstore (in R3 only)
-   Qubes RPC (called at VM startup, or when configuration changed)
-   GUI protocol

xenstore
--------

Keys exposed by dom0 to VM (only Qubes specific included):

-   `qubes-vm-type` - VM type, the same as `type` field in `qvm-prefs`. One of `AppVM`, `ProxyVM`, `NetVM`, `TemplateVM`, `HVM`, `TemplateHVM`
-   `qubes-vm-updatable` - flag whether VM is updatable (whether changes in root.img will survive VM restart). One of `True`, `False`
-   `qubes-timezone - name of timezone based on dom0 timezone. For example `[Europe/Warsaw?](/wiki/SystemDoc/Europe/Warsaw)\`
-   `qubes-keyboard` - keyboard layout based on dom0 layout. Its syntax is suitable for `xkbcomp` command (after expanding escape sequences like `\n` or `\t`). This is meant only as some default value, VM can ignore this option and choose its own keyboard layout (this is what keyboard setting from Qubes Manager does).
-   `qubes-debug-mode` - flag whether VM have debug mode enabled (qvm-prefs setting). One of `1`, `0`
-   `qubes-service/SERVICE_NAME` - subtree for VM services controlled from dom0 (using qvm-service command or Qubes Manager). One of `1`, `0`. Note that not every service will be listed here, if entry is missing, it means "use VM default". List of currently supported services is in [qvm-service man page](/wiki/Dom0Tools/QvmService)
-   `qubes-netmask` - network mask (only when VM has netvm set); currently hardcoded "255.255.255.0"
-   \`qubes-ip - IP address for this VM (only when VM has netvm set)
-   `qubes-gateway` - default gateway IP and primary DNS address (only when VM has netvm set); VM should add host route to this address directly via eth0 (or whatever default interface name is)
-   `qubes-secondary-dns` - secondary DNS address (only when VM has netvm set)
-   `qubes-netvm-gateway` - same as `qubes-gateway` in connected VMs (only when VM serves as network backend - ProxyVM and NetVM); because this is also set as primary DNS in connected VMs, traffic sent to this IP on port 53 should be redirected to DNS server
-   `qubes-netvm-netmask` - same as `qubes-netmask` in connected VMs (only when VM serves as network backend - ProxyVM and NetVM)
-   `qubes-netvm-network` - network address (only when VM serves as network backend - ProxyVM and NetVM); can be also calculated from qubes-netvm-gateway and qubes-netvm-netmask
-   `qubes-netvm-secondary-dns` - same as `qubes-secondary-dns` in connected VMs (only when VM serves as network backend - ProxyVM and NetVM); traffic sent to this IP on port 53 should be redirected to secondary DNS server

