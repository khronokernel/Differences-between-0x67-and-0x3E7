# Differences-between-0x67-and-0x3E7

So you've reading the [Vanilla guide](https://hackintosh.gitbook.io/-r-hackintosh-vanilla-desktop-guide/) but something catches your eye within the guide:

    0x3E7 SIP completely disabled

Some more experienced hackintoshers may be caught off guard by this as we're generally used to seeing 0x67 for disabling System Integrity Protection(SIP) but I'll explain why 0x3E7 is the new preferred value for hackintoshes going forward

# 0x67

Active values:

* CSR\_ALLOW\_UNRESTRICTED\_NVRAM
* CSR\_ALLOW\_UNRESTRICTED\_DTRACE
* CSR\_ALLOW\_TASK\_FOR\_PID
* CSR\_ALLOW\_UNRESTRICTED\_FS
* CSR\_ALLOW\_UNTRUSTED\_KEXTS

# 0x3E7

Active values:

* CSR\_ALLOW\_UNAPPROVED\_KEXTS
* CSR\_ALLOW\_ANY\_RECOVERY\_OS
* CSR\_ALLOW\_DEVICE\_CONFIGURATION
* CSR\_ALLOW\_UNRESTRICTED\_NVRAM
* CSR\_ALLOW\_UNRESTRICTED\_DTRACE
* CSR\_ALLOW\_TASK\_FOR\_PID
* CSR\_ALLOW\_UNRESTRICTED\_FS
* CSR\_ALLOW\_UNTRUSTED\_KEXTS

&#x200B;

What you'll notice is that there's 3 new values added:

* CSR\_ALLOW\_UNAPPROVED\_KEXTS
* CSR\_ALLOW\_ANY\_RECOVERY\_OS
* CSR\_ALLOW\_DEVICE\_CONFIGURATION

The one that's super important to us is UNAPPROVED\_KEXTS as this is what's allowing us to get around MacOS 10.14.5's new [kernel extension notarization](https://developer.apple.com/documentation/macos_release_notes/macos_mojave_10_14_5_release_notes) which can make certain kexts not load correctly through Clover. You can even show what different CsrActiveConfig values enable/disable yourself with CorpNewt's [CsrDecode tool](https://github.com/corpnewt/CsrDecode) or check what other Csr flags there are inside of Apple's [public source code for Darwin](https://github.com/apple/darwin-xnu/blob/master/bsd/sys/csr.h)
