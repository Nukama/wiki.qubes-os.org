---
title: HCL
permalink: /wiki/HCL
---

Hardware Compatibility List for Qubes OS
========================================

The following is a list of systems that have been tested and seem to work fine with Qubes OS

General system requirements
---------------------------

Minimum:

-   4GB of RAM
-   64-bit Intel or AMD processor (x86\_64 aka x64 aka AMD64)
-   Intel GPU strongly preferred (if you have Nvidia GPU, prepare for some [troubleshooting](/wiki/InstallNvidiaDriver); we haven't tested ATI hardware)
-   At least 20GB of disk (Note that **it is possible to install Qubes on an external USB disk**, so that you can try it without sacrificing your current system. Mind, however, that USB disks are usually SLOW!)
-   Fast SSD disk strongly recommended

Additional requirements:

-   Intel VT-x or AMD-v technology (this is needed to run HVM domains only, such as Windows-based AppVMs)
-   Intel VT-d or AMD IOMMU technology (this is needed for effective isolation of your network VMs)
-   TPM with proper BIOS support if you want to use option [​Anti Evil Maid](http://theinvisiblethings.blogspot.com/2011/09/anti-evil-maid.html)

If you don't meet the additional criteria, you can still install and use Qubes. It still offers significant security improvement over traditional OSes, because things such as GUI isolation, or kernel protection do not require special hardware.

**Note:** We don't recommend installing Qubes in a virtual machine!

**Note:** There is a problem with supporting keyboard and mouse on Mac, and so Mac hardware is currently unsupported (patches welcomed!)

Hardware Compatibility List
---------------------------

Device

Qubes R1

Qubes R2

Kernel

Xorg

VT-d

PCI

Kernel

Xorg

VT-x

VT-d

PCI

USB

Lenovo Thinkpad T420

OK

OK

OK

OK

OK

OK

OK

OK

OK

OK

Lenovo Thinkpad T420s

3.2.7+

OK

OK

OK

OK

OK

OK

OK

OK

OK

Lenovo Thinkpad T61
 (Nvidia Quadro NVS 140M)

OK

OK

X

OK

OK

OK

OK

X

OK

OK

Samsung X460

OK

OK

X

OK

OK

OK

OK

X

OK

OK

Sony Vaio Z 12
 (2010 edition)

OK

[OK](https://qubes-os.org/trac/wiki/SonyVaioTinkering)

OK

OK

OK

[OK](https://qubes-os.org/trac/wiki/SonyVaioTinkering)

OK

OK

OK

OK

Dell Latitude E6420
 (Intel HD graphics; Sandy Bridge; i5-2520M)

3.4.18+

OK

OK

OK

3.4.18+

OK

OK

OK

OK

OK
