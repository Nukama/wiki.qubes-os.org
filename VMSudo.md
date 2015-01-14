---
title: VMSudo
permalink: /wiki/VMSudo
---

Password-less root access in VM
===============================

Background ([​/etc/sudoers.d/qubes](http://git.qubes-os.org/?p=qubes-r2/core-agent-linux.git;a=blob;f=misc/qubes.sudoers;hb=HEAD) in VM):

``` {.wiki}
user ALL=(ALL) NOPASSWD: ALL

# WTF?! Have you lost your mind?!
#
# In Qubes VMs there is no point in isolating the root account from
# the user account. This is because all the user data are already
# accessible from the user account, so there is no direct benefit for
# the attacker if she could escalate to root (there is even no benefit
# in trying to install some persistent rootkits, as the VM's root
# filesystem modifications are lost upon each start of a VM).
#
# One might argue that some hypothetical attacks against the
# hypervisor or the few daemons/backends in Dom0 (so VM escape
# attacks) most likely would require root access in the VM to trigger
# the attack.
#
# That's true, but mere existence of such a bug in the hypervisor or
# Dom0 that could be exploited by a malicious VM, no matter whether
# requiring user, root, or even kernel access in the VM, would be
# FATAL. In such situation (if there was such a bug in Xen) there
# really is no comforting that: "oh, but the mitigating factor was
# that the attacker needed root in VM!" We're not M$, and we're not
# gonna BS our users that there are mitigating factors in that case,
# and for sure, root/user isolation is not a mitigating factor.
#
# Because, really, if somebody could find and exploit a bug in the Xen
# hypervisor -- so far there have been only one (!) publicly disclosed
# exploitable bug in the Xen hypervisor from a VM, found in 2008,
# incidentally by one of the Qubes developers (RW) -- then it would be
# highly unlikely if that person couldn't also found a user-to-root
# escalation in VM (which as we know from history of UNIX/Linux
# happens all the time).
#
# At the same time allowing for easy user-to-root escalation in a VM
# is simply convenient for users, especially for update installation.
#
# Currently this still doesn't work as expected, because some idotic
# piece of software called PolKit uses own set of policies. We're
# planning to address this in Beta 2. (Why PolKit is an idiocy? Do a
# simple experiment: start 'xinput test' in one xterm, running as
# user, then open some app that uses PolKit and asks for root
# password, e.g.  gpk-update-viewer -- observe how all the keystrokes
# with root password you enter into the "secure" PolKit dialog box can
# be seen by the xinput program...)
#
# joanna.
```

While ITL still supports above statement, some Qubes users want to enable user/root isolation in VM anyway. We do not support it in any our package, but of course nothing can stop the user from making some modifications in own system.

Below is a complete list of configuration made according to the above statement, with (not necessary complete) list of mechanisms depending on each of them:

1.  sudo (/etc/sudoers.d/qubes):

    ``` {.wiki}
    user ALL=(ALL) NOPASSWD: ALL
    (...)
    ```

    -   easy user-\>root access (main option for the user)
    -   qvm-usb (not really working, as of R2)

2.  PolicyKit (/etc/polkit-1/rules.d/00-qubes-allow-all.rules):

    ``` {.wiki}
    //allow any action, detailed reasoning in sudoers.d/qubes
    polkit.addRule(function(action,subject) { return polkit.Result.YES; });
    ```

    -   NetworkManager configuration from normal user (nm-applet)
    -   updates installation (gpk-update-viewer)
    -   user can use pkexec just like sudo Note: above is needed mostly because Qubes user GUI session isn't treated by [PolicyKit?](/wiki/PolicyKit)/logind as "local" session because of the way in which X server and session is started. Perhaps we will address this issue in the future, but this is really low priority. Patches welcomed anyway.

3.  Empty root password
    -   used for access to 'root' account from text console (xl console) - the only way to access the VM when GUI isn't working
    -   can be used for easy 'su -' from user to root

Dom0 password-less sudo
-----------------------

There is also password-less user-\>root access in dom0. As stated in comment in sudo configuration there (different one than VMs one), there is really no point in user/root isolation, because all the user data (and VM management interface) is already accessible from dom0 user level, so there is nothing more to get from dom0 root account.