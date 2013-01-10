---
title: SoftwareUpdateDom0
permalink: /wiki/SoftwareUpdateDom0
---

Updating software in Dom0
=========================

Why would one want to update software in Dom0?
----------------------------------------------

Normally there should be few reasons for updating software in Dom0. This is because there is no networking in Dom0, which means that even if some bugs will be discovered e.g. in the Dom0 Desktop Manager, this really is not a problem for Qubes, because all the 3rd party software running in Dom0 is not accessible from VMs or network in any way. Some exceptions to the above include: Qubes GUI daemon, Xen store daemon, and disk back-ends (we plan move the disk backends to untrusted domain in Qubes 2.0). Of course we believe this software is reasonably secure and we hope it will not need patching.

However, we anticipate some other situations when updating Dom0 software might be required:

-   Updating drivers/libs for new hardware support
-   Correcting non-security related bugs (e.g. new buttons for qubes manager)
-   Adding new features (e.g. GUI backup tool)

How to do that? (in Beta 2)
---------------------------

Start a console in Dom0 and then run one of the following command:

1) To check and install updates for Dom0 software:

``` {.wiki}
$ sudo qvm-dom0-updates
```

2) To install additional packages in Dom0 (usually not recommended):

``` {.wiki}
$ sudo qvm-dom0-updates anti-evil-maid
```

You can also pass --enablerepo= option in order to enable optional repositories (see yum configuration in Dom0). This is only for advanced users who really understand what they are doing.

### How to downgrade specific package?

1.  Download older version of package:

    ``` {.wiki}
    sudo qubes-dom0-update package-version
    ```

    Yum will say that there is no update, but package will be downloaded to dom0.

2.  Downgrade packge:

    ``` {.wiki}
    sudo yum downgrade package-version
    ```

How to do that? (in Beta 1)
---------------------------

Currently Dom0 update procedure requires command line -- in the future we will make it available from the GUI manager.

First, start the console in Dom0, and switch to root. Then attach Dom0 to the netvm, and run yum update:

``` {.wiki}
$ sudo bash
# qvm-dom0-network-via-netvm up
# yum update
```

Note that by default there is only one repository enabled: ```qubes-dom0-current```.

We strongly recommend to **reboot your system** after Dom0 update.

Alternatively, if you don't want to reboot for some reason, you should not forget about detaching Dom0 from the network:

``` {.wiki}
# qvm-dom0-network-via-netvm down
```

In the future we will modify this update procedure so that it won't require attaching networking to Dom0. Most likely we will use a moderately-trusted system service VM to perform the download of the update rpm via network, and later copy this file to Dom0 using our secure file copy mechanism. Dom0 will then verify the signature on the RPM, and assuming it was ok, will install the rpm.