---
title: HCL
permalink: /wiki/HCL
---

Hardware Compatibility List (HCL) for All Qubes OS Releases
===========================================================

This list contains information about the latest stable release (**R1**) and the latest development release (**R2rc1**). You can also find information about the previous releases (**R2B{1,2,3}**) here.

Generating and Submitting New Reports
-------------------------------------

In order to generate an HCL report in Qubes, simply open a terminal in dom0 (KDE: start-menu -\> System Tools -\> Konsole or Terminal Emulator) and run `qubes-hcl-report <vm-name>`, where `<vm-name>` is the name of the VM to which the generated HCL files will be saved.
 (Note: If you are working with a new Qubes installation, you may need to update your system in order to download this script.)

Users are encouraged to submit their HCL reports for the benefit of further Qubes development and other users. If you would like to submit your HCL report, please send the **HCL Info** `.txt` file to `qubes-users@googlegroups.com` (see [here](/wiki/QubesLists) information about the mailing lists) with the subject `HCL - <your machine model name>`.
 Please include any useful information about any Qubes features you may have tested (see the legend below), as well as general machine compatibility (video, networking, sleep, etc.).
 If you have problems with your hardware, please send the **HCL Support Files** `.cpio.gz` file as well. And try a different kernel in the [Troubleshooting menu](/wiki/InstallationGuideR2rc1#Troubleshooting%20problems%20with%20the%20installer).

**Please note:**
 The **HCL Support Files** may contain numerous hardware details, including serial numbers. If, for privacy or security reasons, you do not wish to make this information public, please **do not** send the `.cpio.gz` file to the public mailing list.

Legend
------

**Legend**

**Marks and background colour**

Yes

Working correctly.

No

Does not work or is not present.

\*

Indicates that some kind of tweaking is needed, see remarks for further information.

 

A blank cell indicates that we lack information about it.

**Columns**

Device

Manufacturer and Devicename
(Socket/CPU, Chipset/Southbridge, Graphics)

BIOS version

Reported BIOS version

[HVM](https://en.wikipedia.org/wiki/Hardware_virtual_machine)

[Intel VT-x](https://en.wikipedia.org/wiki/Intel_VT-x#Intel-VT-x) or [AMD-v](https://en.wikipedia.org/wiki/AMD-V#AMD_virtualization_.28AMD-V.29) technology (required for running HVM domains, such as [Windows-based AppVMs](https://wiki.qubes-os.org/trac/wiki/WindowsAppVms))

[IOMMU](https://en.wikipedia.org/wiki/IOMMU)

Intel VT-d or AMD IOMMU technology (required for effective isolation of network VMs and [PCI passthrough](http://wiki.xen.org/wiki/Xen_PCI_Passthrough))

[TPM](https://en.wikipedia.org/wiki/Trusted_Platform_Module)

TPM with proper BIOS support (required for [Anti Evil Maid](https://wiki.qubes-os.org/trac/wiki/AntiEvilMaid))

Qubes version

Reported Qubes version (R=Release, rc=release candidate, B=Beta, i.e.: R1, R2B1, R2rc1)

[dom0](https://en.wikipedia.org/wiki/Dom0) [kernel](https://en.wikipedia.org/wiki/Linux_kernel#Maintenance)

Reported kernel version (numbers in uname -r), can be selected during installation and boot in Troubleshooting menu.

Remarks

Further information field. Qubes, dom0 and this field is coloured in conjunction to reflect general machine compatibility.

Reported by

Name linked to report in [qubes-users.](https://groups.google.com/forum/#!forum/qubes-users)

**Note:**
 The HCL is a compilation of reports generated and submitted by users. Except in the case of developer-reported entries, the Qubes team has not independently verified the accuracy of these reports.
 If using the list to make a purchasing decision, we recommend that you first consult the datasheets (CPU, chipset, motherboard) for particular support of:

-   HVM ("AMD virtualization (AMD-V)", "Intel virtualization (VT-x)", "VIA virtualization (VIA VT)")
-   IOMMU ("AMD I/O Virtualization Technology (AMD-Vi)", "Intel Virtualization Technology for Directed I/O (VT-d)")
-   TPM ("Trusted Plaform Module (TPM)" connected to a "20-pin TPM header" on motherboards.)

and test the hardware yourself, if possible.
 Try to shop for hardware with best achievable Qubes security level (green columns in HVM, IOMMU, TPM) and general machine compatibility (green columns in Qubes version, dom0 kernel, remarks).

Reports
-------

Qubes HCL
=========

Device

BIOS version

HVM

IOMMU

TPM

**Qubes version**

dom0 kernel

Remarks

Reported by

**Laptop Devices**

Apple MacBookPro
 (i5-3210M, Ivy Bridge, Intel HD Graphics)

Yes

Yes

R2B2

[​read more](https://groups.google.com/d/topic/qubes-users/ZbjrseLxuPQ/discussion)

[​ph145h](https://groups.google.com/d/msg/qubes-users/ZbjrseLxuPQ/5Jx5DvpnwMMJ)

Apple MacBookPro
 (i7-620M, HD Graphics + GT 330M)

Yes

No

R2B2

No Network, Chipset doesn't support VT-d! [​read more](https://groups.google.com/d/topic/qubes-devel/hag-MQDH_Vs/discussion) [​read more](https://groups.google.com/d/topic/qubes-devel/hag-MQDH_Vs/discussion)

[​Alex Dubois](https://groups.google.com/d/msg/qubes-devel/hag-MQDH_Vs/pmJ7TIWUWAsJ)

Asus N56VZ
 (CPU, HM67 Express, HD Graphics)

N56VZ.216

Yes

No

R2rc2

3.12.23-1

Chipset does not support VT-d

[Oleg Artemiev](https://groups.google.com/d/msg/qubes-users/KOBFFMJrvRw/JUB-TAoGwr8J)

ASUS X55A
 ()

No

No

R2B2

[​read more](https://groups.google.com/d/topic/qubes-devel/2csjvHia9Rw/discussion)

[​Zrubi](https://groups.google.com/d/msg/qubes-devel/2csjvHia9Rw/NRsqR0g6wIMJ)

ASUS Zenbook UX-31
 (i5-2557M, HD 3000)

Yes

Yes

R2B2

[​read more](https://groups.google.com/d/topic/qubes-devel/6I07Bbzn5M4/discussion)

[​Stephen Boyd](https://groups.google.com/d/topic/qubes-devel/6I07Bbzn5M4/discussion)

ASUS Zenbook UX31A
 (i5-3317U, Ivy Bridge, HD4000)

UX31A.212

Yes

Yes

R2rc1

3.12.14-4

USB Ethernet dongle not working.

[Darren Thurston](https://groups.google.com/d/msg/qubes-users/WFukA9TlQog/fua6-o89AEoJ)

ASUS Zenbook UX31A
 (i7-3517U, Ivy Bridge, HD4000)

UX31A.212

Yes

Yes

R2B3

3.11.1-2

Backlight keyboard keys not working. Only 4GB ram, but works.

[jeff](https://groups.google.com/d/msg/qubes-users/jlvKvKtEiWk/axMMx8St8xIJ)

Clevo P150EM (Sager NP9150)
 (i7-3720QM, HD4000)

4.6.5

Yes

Yes

R2B3

3.9.2-2

Most features work on 3.7 and 3.11, but for best results use 3.9.

[​AndrewX192](https://groups.google.com/d/msg/qubes-users/Ol6v6xSla4Y/vFgIHeObF-8J)

Clevo P151HM1
 (i7-2720QM, Sandy Bridge, GeForce GTX 460M)

4.6.4

Yes

Yes

No

R2rc1

3.12.14-4

[​David Kennedy](https://groups.google.com/d/msg/qubes-users/a5dspO8wRCU/RC12tcxtaCcJ)

Clevo W150ER
 (i7-3612QM, Ivy Bridge, Geforce GT 650M)

4.6.5

Yes

No

R2rc1

3.12.14-4

[​chymian](https://groups.google.com/d/msg/qubes-users/YOE2ds6RVWc/n24INxfu11gJ)

Dell Inspiron 3521
 (i3-3217U, HM76, HD Graphics)

A12

Yes

No

R2rc1

3.12.14-4

[​NetVM hangs computer](https://groups.google.com/d/msg/qubes-users/SgUAMvUizp0/WND6yZtYP5cJ)

[​Nikita Mikhailov](https://groups.google.com/d/msg/qubes-users/SgUAMvUizp0/WND6yZtYP5cJ)

Dell Latitude E4300
 (P9600, GMA 4500MHD, Mobile 4 Series Chipset)

A24

Yes

Yes

R2B2

[​read more](https://groups.google.com/d/topic/qubes-devel/LNJqSbH0cOQ/discussion)

[​Pablo Costa](https://groups.google.com/d/msg/qubes-devel/LNJqSbH0cOQ/VC9EwEDrXMQJ)

R2B3

3.9

Runs only with kernel 3.9 [​read more](https://groups.google.com/d/topic/qubes-devel/LNJqSbH0cOQ/discussion)

[​Pablo Costa](https://groups.google.com/d/msg/qubes-devel/LNJqSbH0cOQ/VC9EwEDrXMQJ)

Dell Latitude 5520
 ()

Yes

R1

[​read more](https://groups.google.com/group/qubes-devel/msg/7418e7084c2de99f?hl=en)

[​Erik Edin](https://groups.google.com/group/qubes-devel/msg/7418e7084c2de99f?hl=en)

Dell Latitude E6320
 (i5-2540M, Sandy Bridge, HD graphics)

A06

Yes

Yes

R2B2

[​read more](https://groups.google.com/d/topic/qubes-users/FyA7_Kzw1WA/discussion)

[Alex​](https://groups.google.com/d/msg/qubes-users/F-jVh62ANak/s57rqUWTY7kJ)

Dell Latitude E6420
 (i5-2520M, Sandy Bridge, HD graphics)

Yes

Yes

R1

3.4.17

needs kernel 3.4.17+

[​Qubes core developers]()

R2B1

3.4.17

needs kernel 3.4.17+

[​Qubes core developers]()

R2B2

3.7.4

Suspend doesn't work on 3.7.6 kernel, but work on 3.7.4

[​Qubes core developers]()

R2B3

3.11.1-2

[marmarek (Qubes core developer)](https://groups.google.com/d/msg/qubes-devel/S-leNH8AYsU/WL_XdNAhBkQJ)

Dell Latitude E6430
 (i5-3340M, Ivy Bridge, HD graphics)

A11

Yes

Yes

R2B2

3.7.4

[​Zrubi](https://groups.google.com/d/msg/qubes-users/pAVGe04ZC48/AJwY6yd7LeIJ)

R2B3

3.7.4

[​Zrubi](https://groups.google.com/d/msg/qubes-users/pAVGe04ZC48/AJwY6yd7LeIJ)

R2rc1

3.12.14

The optional nVidia Optimus VGA is still not working.

[​Zrubi](https://groups.google.com/d/msg/qubes-users/sfV4-pMWrBY/qiHlnnza9a0J)

Dell Latitude E6520
 ()

Yes

R1

[​read more](https://groups.google.com/group/qubes-devel/msg/340afc6fc2d06d0e)

[​Steven Collins](https://groups.google.com/group/qubes-devel/msg/340afc6fc2d06d0e)

Dell Precision M4600
 (i7-2860QM, NVIDIA Quadro 1000M)

Yes

R1

[​nqe](https://groups.google.com/group/qubes-devel/browse_thread/thread/ddf35d12a35f96a3)

Dell XPS 13
 (i5, Sandy Bridge, Intel HD)

A03

R1

[​j](https://groups.google.com/d/msg/qubes-devel/7JumqdldVJM/n9TiDVxc2jkJ)

R2B1

[​read more](https://groups.google.com/d/msg/qubes-devel/7JumqdldVJM/n9TiDVxc2jkJ)

[​j](https://groups.google.com/d/msg/qubes-devel/7JumqdldVJM/n9TiDVxc2jkJ)

R2B2

[​read more](https://groups.google.com/d/msg/qubes-devel/jamRkZJDC0g/KTniY0Y3dioJ)

[​j](https://groups.google.com/d/msg/qubes-devel/7JumqdldVJM/n9TiDVxc2jkJ)

Dell XPS 13 (L322X)
 (i7-3537U, Ivy Bridge, Intel HD)

A09

Yes

No

R2B2

[​read more](https://groups.google.com/d/topic/qubes-users/21kqNBzJLPw/discussion)

[​Brian J Smith-Sweeney](https://groups.google.com/d/msg/qubes-users/21kqNBzJLPw/e74SMRweTMsJ)

Fujitsu S751
 (i5-2520M, QM67, HD3000)

1.18

Yes

Yes

R1

[​Zrubi](https://groups.google.com/forum/#!msg/qubes-devel/xoyNCigBvFE/ER61L6TbVpwJ)

R2B1

[​Zrubi](https://groups.google.com/forum/#!msg/qubes-devel/xoyNCigBvFE/ER61L6TbVpwJ)

R2B2

3.7.4

needs kernel downgrade to 3.7.4

[​Zrubi](https://groups.google.com/forum/#!msg/qubes-devel/xoyNCigBvFE/ER61L6TbVpwJ)

R2B3

3.7.4

[​Zrubi](https://groups.google.com/forum/#!msg/qubes-devel/xoyNCigBvFE/ER61L6TbVpwJ)

HP EliteBook 2170p
 (i5-3317U, Ivy, Intel HD Graphics)

68IMT Ver. F.42

Yes

Yes

R2rc2

3.12.23-1

[​read more](https://groups.google.com/d/topic/qubes-users/q5M9KbPatEA/discussion)

[Dimiter Georgiev](https://groups.google.com/d/msg/qubes-users/q5M9KbPatEA/fXIZ-yvJVA8J)

HP EliteBook 820 G1
 (i5-4300U, Haswell, Intel HD Graphics)

L71 Ver. 01.11

Yes

Yes

R2rc2

3.12.23-1

[​read more](https://groups.google.com/d/topic/qubes-users/8s98SegfdbI/discussion)

[Mihai Genescu](https://groups.google.com/d/msg/qubes-users/8s98SegfdbI/pIOWgeJSuSAJ)

HP EliteBook 8540p
 (i5-2540M, Arrandale, NVIDIA GT216)

F.0C

Yes

Yes

R2B2

[​read more](https://groups.google.com/d/topic/qubes-users/o_FTsPW6GD8/discussion)

[Olivier Médoc](https://groups.google.com/d/msg/qubes-users/o_FTsPW6GD8/bjAD-CSpRKsJ)

HP EliteBook 8560p
 (i5-2540M, Sandy Bridge, ATI Caicos)

F.08

Yes

Yes

R2B2

[​read more](https://groups.google.com/d/topic/qubes-users/o_FTsPW6GD8/discussion)

[Olivier Médoc](https://groups.google.com/d/msg/qubes-users/o_FTsPW6GD8/bjAD-CSpRKsJ)

HP EliteBook Folio 9470m
 (i5-3437U, Ivy Bridge, HD graphics)

68IBD Ver. F.47

R2

3.12.23-1

no access to BIOS on this machine

[Paolo Righi](https://groups.google.com/d/msg/qubes-users/iup1MmBFx8Q/hCCAOVwrB2kJ)

HP Pavilion Sleekbook 14-B030TU
 (i5-3317U, Ivy Bridge, Intel HD Graphics)

F.06

Yes

Yes

R2B1

[​read more](https://groups.google.com/d/topic/qubes-devel/ZC_SQJhXVOM/discussion)

[​Stephen Boyd](https://groups.google.com/d/msg/qubes-devel/ZC_SQJhXVOM/4aLjEc7GIsUJ)

R2B2

[Stephen Boyd](https://groups.google.com/d/msg/qubes-devel/ZC_SQJhXVOM/4aLjEc7GIsUJ)

Lenovo IdeaPad Y580
 (unknown, HM76 Express, HD Graphics)

No

R2rc2

3.12.23-1

Not able to install, HM76 Express Chipset does \*not\* support VT-d

[johny jj2](https://groups.google.com/d/msg/qubes-users/l542hyu8gqk/IjTjjcfGvKsJ)

Lenovo IdeaPad Z500 Touch (20221)
 (i5-3230M, Ivy Bridge, HD Graphics)

1.21

Yes

No

R2

3.12.18-1

Touchpad doesn't work during installer

[Rowan Crane](https://groups.google.com/d/msg/qubes-users/6U_Qm3-Edg0/Aioi8lSBR3wJ)

Lenovo Thinkpad Edge E130
 (i3-3217U, Ivy Bridge, HD Graphics)

2.05

Yes

Yes

R2B2

[Danny Cautaert](https://groups.google.com/d/msg/qubes-devel/kGnZKZ9ILKA/2vpzltNW3K4J)

Lenovo Thinkpad T60
 (T7600, GMA 950)

Yes

No

R2rc2

Does not install

[saltykremlin](https://groups.google.com/d/msg/qubes-users/cpIE1ybuwoA/HDriMPH0vGcJ)

Lenovo Thinkpad T61
 (Nvidia Quadro NVS 140M)

Yes

No

R1

[​Qubes core developers]()

R2B1

[​Qubes core developers]()

R2B3

3.11.1-2

[​Qubes core developers]()

Lenovo Thinkpad T410 (2522AC1)
 (i5-520M, Arrandale, HD graphics)

1.32

Yes

Yes

Yes

R2rc1

3.12.14-4

AEM works

[​Vincent Penquerc'h](https://groups.google.com/d/msg/qubes-users/68PRfx5FteY/H6rvQ6ojEysJ)

Lenovo Thinkpad T410 (2516CTO)
 (i7-620M, Arrandale, HD graphics)

1.34

Yes

Yes

R2B3

3.9

[​Vincent Penquerc'h](https://groups.google.com/d/msg/qubes-users/WsHQ_GqXdT4/63xtC0iqXXEJ)

Lenovo Thinkpad T420
 ()

Yes

Yes

Yes

R1

[​Qubes core developers]()

R2B1

AEM works

[​Qubes core developers]()

Lenovo Thinkpad T420s
 (i5-2520M, Sandy Bridge, Intel HD graphics)

Yes

Yes

Yes

R1

[​Qubes core developers]()

R2B1

AEM works

[​Qubes core developers]()

R2B2

Requires kernel 3.2.30 to support S3 sleep (the default kernel S3 sleep causes system reboot)

[​Qubes core developers]()

R2B3

3.11

[​Qubes core developers]()

Lenovo Thinkpad T430
 (i5-3320)

Yes

Yes

R2B1

[​Tunguuz](https://groups.google.com/d/msg/qubes-devel/S_VG_jgtpBo/VngCPK2W5FcJ)

Lenovo Thinkpad T430
 (i5-3360M, Ivy Bridge, HD Graphics)

2.5.1

Yes

Yes

R2B2

[​read more](https://groups.google.com/d/topic/qubes-devel/LSVluAZ9Udo/discussion)

[Alex Dubois](https://groups.google.com/d/msg/qubes-devel/LSVluAZ9Udo/Fl3jmt4tWssJ)

Lenovo Thinkpad T430s
 (i5-3320M, QM77, HD4000)

2.05

Yes

Yes

R2B1

[​read more](https://groups.google.com/d/topic/qubes-devel/Z9seyOT46Ro/discussion)

[​cprise](https://groups.google.com/d/msg/qubes-devel/Z9seyOT46Ro/wX6tsrxE84sJ)

R2B2

[read more](https://groups.google.com/d/topic/qubes-users/V4PQYEBuoSg/discussion)

[cprise](https://groups.google.com/d/msg/qubes-users/V4PQYEBuoSg/udLCHyR6RUUJ)

R2B3

3.11

[​cprise](https://groups.google.com/d/msg/qubes-users/Ll_pPP7glwI/jtRbKtQO_rMJ)

2.58

R2rc1

3.12.14-4

[​cprise](https://groups.google.com/d/msg/qubes-users/452tkVCzvOw/_dQ8DXaDzp0J)

Lenovo Thinkpad T430u
 (i7-3517M, Ivy Bridge, HD Graphics + GT 620M)

2.08

Yes

Yes

R2B1

[​read more](https://groups.google.com/d/topic/qubes-devel/Z9M_k3i6dxU/discussion)

[tigerbeard](https://groups.google.com/d/msg/qubes-devel/Z9M_k3i6dxU/09CqBppyMnsJ)

Lenovo Thinkpad T440p
 (i7-4800MQ, Haswell, Intel HD graphics)

2.21

Yes

Yes

R2B3

3.11

802.11 ac doesn't work with Fedora 18, but with Fedora 20

[​7v5w7go9ub0o](https://groups.google.com/d/msg/qubes-users/r6kC4YHgDjM/yJXpvIdoWkUJ)

Lenovo Thinkpad T500
 (P8400, GM45, GMA 4500MHD)

3.22

Yes

\*

R2B3

3.11.1-2

activated VT-d BIOS option not recognized in Qubes

[​Jens Porup](https://groups.google.com/d/msg/qubes-users/EoG4VffajRw/-oeSfNCA-KIJ)

Lenovo Thinkpad T510 (4384-WGZ)
 (i5-520M, Arrandale, Intel HD graphics)

1.52

Yes

Yes

R2B3

3.9.2

[​pete](https://groups.google.com/d/msg/qubes-users/UP9BK_yn-Pk/DR6PBVF4GlgJ)

R2rc1

3.9.2

Audio is always muted after reboot

[​pete](https://groups.google.com/d/msg/qubes-users/4ASK0cBfMM0/11U7Zx-f7HwJ)

Lenovo Thinkpad W510
 (i7-Q820, nVidia)

Yes

R1

[​read more](https://groups.google.com/forum/#!msg/qubes-devel/TgDWwBs36yA/IUFZPHs716cJ)

[​Sebastian Hültenschmidt](https://groups.google.com/forum/#!msg/qubes-devel/TgDWwBs36yA/IUFZPHs716cJ)

Lenovo Thinkpad W530 (24385JU)
 (i7-3740QM, nVidia Optimus)

2.53

Yes

Yes

R2rc1

3.12.18-1

display issues[​read more](https://groups.google.com/d/msg/qubes-users/ReLqPcsvDwk/WbJdDUBqgTsJ)

[​Lab Man](https://groups.google.com/d/msg/qubes-users/ReLqPcsvDwk/WbJdDUBqgTsJ)

Lenovo Thinkpad X1 Carbon (3444CTO)
 (i5-3427U)

Yes

Yes

R2B2

[Ulrich Pfeifer](https://groups.google.com/d/msg/qubes-users/UCuF41rq758/BRhc7lTecsMJ)

Lenovo X1 Carbon Gen 2
 (i5-4300U, Haswell-ULT, HD4000)

1.07

No

No

R2B3

3.11.1-2

needs iwl7260-firmware in netvm

[​Patrick Schless](https://groups.google.com/d/msg/qubes-users/cu_mJa4iDHk/v1FdT3ZGofEJ)

Lenovo X1 Carbon Gen 2
 (i7-4600U, Haswell-ULT, HD4000)

1.11

Yes

Yes

R2B3

3.11.1-2

needs iwl7260-firmware in netvm

[​Jean-François Rioux](https://groups.google.com/d/msg/qubes-users/cu_mJa4iDHk/v1FdT3ZGofEJ)

Lenovo Thinkpad X61t
 ()

R2B1

[​George Walker](https://groups.google.com/d/msg/qubes-devel/4IrF1A6sa3U/QIQe-dNc4tEJ)

Lenovo Thinkpad X201
 (i5-520M, HD3000)

Yes

Yes

R2rc1

3.9.2-2

X problem with activated VT-d on all other kernel versions

[​Joonas Lehtonen](https://groups.google.com/d/msg/qubes-users/z5BEjSuR7VE/CD2JMeAhDaoJ)

Lenovo Thinkpad X220 (4290-W3W)
 (i5-2520M, QM67, HD3000)

1.39

Yes

Yes

R1

[​Stefan Boresch](https://groups.google.com/group/qubes-devel/msg/f41578eef913446a)

R2B2

[​read more](https://groups.google.com/d/topic/qubes-users/-b8b9fpo0UU/discussion)

[​Matt Tracy](https://groups.google.com/d/msg/qubes-users/-b8b9fpo0UU/RFh6HiWqt5oJ)

R2B3

3.11.1-2

[​Matt Tracy](https://groups.google.com/d/msg/qubes-users/5tNavg4MhT4/dFXsYHXOgu4J)

Lenovo Thinkpad X230
 (i5-3320M, Ivy Bridge, HD Graphics)

2.5.1

Yes

Yes

R1

[​read more](https://groups.google.com/d/msg/qubes-devel/XN6JrEXVOVA/lkxGRA00EqgJ)

[​Chris](https://groups.google.com/d/msg/qubes-devel/XN6JrEXVOVA/lkxGRA00EqgJ)

R2B2

[​read more](https://groups.google.com/d/topic/qubes-users/hf0vkL3TE7k/discussion)

[​mgflax](https://groups.google.com/d/msg/qubes-users/hf0vkL3TE7k/VOtrW3wEbtMJ)

Lenovo Thinkpad X230 (2306CTO)
 (i7-3520M, Ivy Bridge, HD Graphics)

2.54

Yes

Yes

R2rc1

3.12.14-4

[​read more](https://groups.google.com/d/msg/qubes-users/NXIL5rEh65o/rCBf1PYr2jsJ)

[​Franz Felix](https://groups.google.com/d/msg/qubes-users/NXIL5rEh65o/rCBf1PYr2jsJ)

Lenovo Yoga 2
 (i3-4010U, Haswell, HD Graphics)

96CN23WW(V1.09)

Yes

Yes

R2

3.12.23-1

required patching for working wifi

[Vadim](https://groups.google.com/d/msg/qubes-users/3WdYjv4QHIc/YIWiyoWDFBkJ)

MSI GP60-2PE
 (i5-4200H, Haswell, HD Graphics)

E16GHIMS.109

Yes

Yes

R2rc2

3.12.23-1

speep doesn't work

[Fabian Wloch](https://groups.google.com/d/msg/qubes-users/X0KB-euVJgc/1Aqcb_aNtB0J)

MSI GS60
 (i7-4700HQ, Haswell, IGP)

E16H2IMS.103

Yes

Yes

R2rc1

3.12.18-1

[​Rudd-O](https://groups.google.com/d/msg/qubes-users/Sz0Nuhi4N0o/jIjFnf2XCKUJ)

MSI GX660
 (i5-460M, PM55, Radeon HD5870)

1.0L

Yes

No

R2B3

3.11.1-2

[​Avant Garden](https://groups.google.com/d/msg/qubes-users/UrWYjkHwon8/TPE0XSBiPDQJ)

Samsung NP300E7A
 (i3-2330M, HM65, HD3000)

P04ABJ

Yes

No

R2B3

3.11.1-2

[​Marc](https://groups.google.com/d/msg/qubes-users/dzYwiYzvWYM/iOyq3V2y5L4J)

Samsung Series 7 Chronos NP700Z5C
 (i7-3635QM, nVidia Optimus)

P04ABJ

Yes

No

R1

[​read more](https://groups.google.com/d/msg/qubes-devel/0xBeX8NZFiU/bUqxGdn6KOMJ)

[​Outback Dingo](https://groups.google.com/d/msg/qubes-devel/0xBeX8NZFiU/bUqxGdn6KOMJ)

R2B1

[​read more](https://groups.google.com/d/msg/qubes-devel/0xBeX8NZFiU/bUqxGdn6KOMJ)

[​Outback Dingo](https://groups.google.com/d/msg/qubes-devel/0xBeX8NZFiU/bUqxGdn6KOMJ)

R2B2

[​read more](https://groups.google.com/d/topic/qubes-devel/Wu1mn9f1qgM/discussion)

[​Outback Dingo](https://groups.google.com/d/msg/qubes-devel/0xBeX8NZFiU/bUqxGdn6KOMJ)

Samsung X460
 (P8600, PM45, GeForce 9200M GS)

20091110

Yes

No

R1

[​Qubes core developers]()

R2B1

[​Qubes core developers]()

R2B3

3.11.1-2

[marmarek (Qubes core developer)](https://groups.google.com/d/msg/qubes-devel/S-leNH8AYsU/WL_XdNAhBkQJ)

Sony VAIO Z 12
 (2010 edition)

Yes

Yes

R1

[read more](/trac/wiki/SonyVaioTinkering)

Qubes core developers

R2B1

[read more](/trac/wiki/SonyVaioTinkering)

Qubes core developers

R2B2

[read more](/trac/wiki/SonyVaioTinkering)

Qubes core developers

R2B3

3.11

[read more](/trac/wiki/SonyVaioTinkering)

Qubes core developers

Sony VAIO series Z2 - VPCZ2190S
 (i5-2540M, Sandy Bridge, HD3000, 2011 edition)

Yes

\*

R1

[​read more](https://groups.google.com/d/msg/qubes-devel/xoyNCigBvFE/fkC6em-Wqd0J)

[​Danny Fullerton](https://groups.google.com/d/msg/qubes-devel/xoyNCigBvFE/fkC6em-Wqd0J)

R0170H5

Yes

R2B3

3.11

BIOS has to be patched to activate VT-d, external Radeon HD 6700M

[​Danny Fullerton](https://groups.google.com/d/msg/qubes-users/8urk8ZNeblg/jCD2iQyQQZwJ)

Toshiba M780 S7240
 ()

latest

Yes

R1

[​Franz](https://groups.google.com/d/msg/qubes-devel/Zul8mQoI2OI/-jzfJL2fV84J)

Toshiba Tecra A11-15X
 (i7-M620)

Yes

R1

[​PirBoazo](https://groups.google.com/d/msg/qubes-devel/wNX2oz1nK2I/YI5ro4NMppgJ)

Toshiba Tecra S11
 ()

Yes

R1

[​read more](https://groups.google.com/group/qubes-devel/browse_thread/thread/fdec0ec165a87726)

[​Jan Beerden](https://groups.google.com/group/qubes-devel/browse_thread/thread/fdec0ec165a87726)

Zareason Ultra Lap 420
 (i5-3317U, Ivy Bridge, HD Graphics)

Yes

Yes

R2B2

[​Ant](https://groups.google.com/d/msg/qubes-users/uKI-VBtKWxg/uKjsdGNSpSQJ)

**Desktop, Workstation and Server**

Dell Inspiron 660
 (i5-3330, Xeon E3-1200 Graphics)

A09

Yes

Yes

R2B2

[read more](https://groups.google.com/d/topic/qubes-users/Nq7T0l4A2b0/discussion)

[KR](https://groups.google.com/d/msg/qubes-users/Nq7T0l4A2b0/IP_pwZMn9LYJ)

Dell PowerEdge T110 II
 (Xeon E3-1230, onboard Matrox)

Yes

R1

[​Geoff](https://groups.google.com/group/qubes-devel/msg/8a894915909eeaee)

Dell Precision T3400 Workstation
 (Intel Q6600, NVIDIA Quadro NVS 290)

A09

Yes

No

R2B2

[Andrew Sorensen](https://groups.google.com/d/msg/qubes-devel/D16dM3rg8Iw/zOEZmjTJkRIJ)

HP Compaq dc7800 SFF
 (E8400, Q35)

1.32

Yes

\*

\*

R2B3

3.9.2-2

IGP won't work with activated VT-d (3.12,3.11,3.7), [​3,9 works](https://groups.google.com/d/msg/qubes-users/QmshQ6aHsCM/LTyn6mL0kFkJ), TPM not tested.

[​Rob Townley](https://groups.google.com/d/msg/qubes-users/QmshQ6aHsCM/nJv69i3jbWYJ)

HP Compaq dc7900 Convertible Minitower
 (E8400, Q45/Q43)

1.26

Yes

Yes

R2B3

3.9.2-2

Problem with graphics on 3.11,3.7, only 2GB RAM.

[​Nukama](https://groups.google.com/d/msg/qubes-users/RYzkSFoMsxQ/ukXhBW4ybqQJ)

R2rc1

3.9

Problem with graphics on 3,12,3.11,3.7, only 2GB RAM stock.

[​Nukama](https://groups.google.com/d/msg/qubes-users/RYzkSFoMsxQ/ukXhBW4ybqQJ)

HP ProLiant DL360 G5
 (E5440, 5000P, ATI ES1000)

P58

Yes

No

R2B3

3.11.1-2

Some video glitches, no audio hardware.

[​Nukama](https://groups.google.com/d/msg/qubes-users/1CyVEStoVCI/RTRw8-aalsUJ)

Lenovo ThinkCentre M71e
 (G620, H61, HD2000)

9QKT29AUS

Yes

No

R2B3

3.11.1-2

[​Nukama](https://groups.google.com/d/msg/qubes-users/YcqMDcVYQh8/pk0B_9RfGQMJ)

Lenovo ThinkStation S30 4352G1G
 (E5-1620 v2, Ivytown, Radeon HD 6950)

A2KT44AUS

Yes

Yes

\*

R2rc1

3.12.14-4

Issue with sound, network and marvel raid. AEM untested.

[​Hans Walter](https://groups.google.com/d/msg/qubes-users/EDxALP9GNFo/gAH7nZXd0CkJ)

**Motherboards**

ASRock G31M-GS
 (LGA775, G31, GMA3100)

P1.90

Yes

No

R2rc1

3.12.14-4

using Q6600 and GeForce 8600 GT

[​fb900c26](https://groups.google.com/d/msg/qubes-users/jxVnfMnU4s4/5t_lbe3oA7IJ)

ASRock Q87M Vpro
 (LGA1150, Q87)

P1.50

Yes

Yes

R2B3

3.11.1-2

Problems with Power Saving, Audio and USB3

[​suricabile](https://groups.google.com/d/msg/qubes-users/oExJBIDsAwQ/lwAzNNe7OcYJ)

ASRock Z77 Pro4
 (i7-3770, Ivy Bridge, HD Graphics 4000)

P1.40

Yes

Yes

R2B2

[read more](https://groups.google.com/d/topic/qubes-users/lycnE-LcJBo/discussion)

[gorka](https://groups.google.com/d/msg/qubes-users/lycnE-LcJBo/0u10xl7AMrIJ)

Asus M4A89GTD USB3/PRO
 ()

3029

Yes

No

No

R2rc1

with Phenom II X4 965 and Radeon HD 5750

[David Kennedy](https://groups.google.com/d/msg/qubes-users/6UPz3B0hg_U/bNcRAMiYJekJ)

Biostar A880GZ
 (AM3+, 880G/SB850)

R2B3

3.9.2-2

[\#762](/trac/ticket/762)

[​clewis](https://groups.google.com/d/msg/qubes-users/DTot3wX1-nQ/cpCsRfs5PfgJ)

Biostar TA790GX A3+
 (AM3, 790GX/SB750)

78DAA420

Yes

No

R2B3

3.9.2-2

[\#762](/trac/ticket/762)

[​Nukama](https://groups.google.com/d/msg/qubes-users/DTot3wX1-nQ/229c20xWrdQJ)

R2rc1

3.12.14-4

USB-Devices are working in 3.12 installer and luks prompt again.

[​Nukama](https://groups.google.com/d/msg/qubes-users/DTot3wX1-nQ/229c20xWrdQJ)

EVGA\_E685
 (LGA1150, Z68)

4.6.4

Yes

No

R2B3

3.11.1-2

Problems with Audio

[​jeff](https://groups.google.com/d/msg/qubes-users/wSCL-4VL2Ew/cU8-2qyT008J)

GIGABYTE GA-6PXSV4
 (Xeon E5, C604, Aspeed AST2300)

R17

Yes

Yes

\*

R2

3.12.23-1

TPM header available

[Nukama](https://groups.google.com/d/msg/qubes-users/yveUu94j26U/40sJaykesaEJ)

Gigabyte GA-870A-UD3
 (Phenom II X4 955, 870/SB850, GTX 460)

F5a

Yes

No

R2B2

3.11.1-2

[Fabian Lichte](https://groups.google.com/d/msg/qubes-users/S4Ju0zDM2mI/Q4GZ4S2txdMJ)

R2rc1

3.12.14-4

[Fabian Lichte](https://groups.google.com/d/msg/qubes-users/S4Ju0zDM2mI/Q4GZ4S2txdMJ)

Gigabyte GA-FXA990-UD3 (rev 3.0)
 (AMD FX-8350, GTX 470)

FB

Yes

\*

\*

R2B2

IOMMU not tested with Qubes, working on other platforms [read more](https://groups.google.com/d/msg/qubes-devel/qXct-TU4tKs/_JEtbQCyHl8J), TPM header

[m astroj](https://groups.google.com/d/msg/qubes-devel/oox94EsIduQ/7w4xUoK5pxwJ)

Gigabyte GA-X79S-UP5 Wi-Fi
 (LGA2011, C606)

1.0

Yes

\*

\*

IOMMU not tested with Qubes, VT-d option in BIOS according to [manual](http://download.gigabyte.eu/FileList/Manual/mb-manual_ga-x79s-up5_e.pdf), TPM header

MSI Big Bang
 (i7-950, Radeon HD 6770)

R2B2

[read more](https://groups.google.com/d/topic/qubes-devel/TxzaoodB02o/discussion)

[Andrew Sorensen](https://groups.google.com/d/msg/qubes-devel/TxzaoodB02o/NxVHjaPoRYoJ)

Supermicro X10SAE
 (Xeon E3-1245, Haswell)

1.0

Yes

Yes

\*

R1

TPM header

[​Qubes Fan](https://groups.google.com/d/msg/qubes-users/V9BLpdf4xCs/v4XcOjLT6uUJ)

R2B2

[​Qubes Fan](https://groups.google.com/d/msg/qubes-users/V9BLpdf4xCs/v4XcOjLT6uUJ)


