---
title: CopyingFiles
permalink: /wiki/CopyingFiles
---

Copy and Paste between domains
==============================

Qubes fully supports secure copy and paste operation between domains. In order to copy a clipboard from domain A to domain B, follow those steps:

1.  Click on the application window in the domain A where you have selected text for copying. Then use the *app-specific* hot-key (or menu option) to copy this into domain's local clipboard (in other words: do the copy operation as usual, in most cases by pressing Ctrl-C).
2.  Then (when the app in domain A is still in focus) press Ctrl-Shit-C magic hot-key. This will tell Qubes that we want to select this domain's clipboard for *global copy* between domains.
3.  Now select the destination app, running in domain B, and press Ctrl-Shift-V, another magic hot-key that will tell Qubes to make the clipboard marked in the previous step available to apps running in domain B. This step is necessary because it ensures that only domain B will get access to the clipboard copied from domain A, and not any other domain that might be running in the system.
4.  Now, in the destination app use the app-specific key combination (usually Ctrl-V) for pasting the clipboard.

Note that the global clipboard will be cleared after step \#3, to prevent accidental leakage to another domain, if the user accidentally pressed Ctrl-Shift-V later.

This 4-step process might look complex, but after some little practice it really is very easy and fast. At the same time it provides the user with full control over who has access to the clipboard.

On Copy/Paste Security
----------------------

The scheme is *secure* because it doesn't allow other VMs to steal the content of the clipboard. However, one should keep in mind that performing a copy and paste operation from *less trusted* to *more trusted* domain can always be potentially insecure, because the data that we insert might potentially try to exploit some hypothetical bug in the destination VM (e.g. the seemingly innocent link that we copy from untrusted domain, might turn out to be, in fact, a large buffer of junk that, when pasted into the destination VM's word processor could exploit a hypothetical bug in the undo buffer). This is a general problem and applies to any data transfer between *less trusted to more trusted* domain. It even applies to copying files between physically septate machines (air-gapped) systems. So, you should always copy clipboard and data only from *more trusted* to *less trusted* domains.

See also [​this article](http://theinvisiblethings.blogspot.com/2011/03/partitioning-my-digital-life-into.html) for more information on this topic, and some ideas of how we might solve this problem in some future version of Qubes.
