# Awesome Ageless FLOSS

*Translations: [Català](README.ca.md)*

A curated list of Free/Libre Open Source Software projects, not all at the OS-level, that stand for computers obeying their human mandate and thus oppose age verification and age gating laws.

This list is maintained by [Protecció de la Frontera Electrònica](https://fronteraelectronica.cat), a [Catalan](https://en.wikipedia.org/wiki/Catalan_Republic) organization fighting for digital rights which believes that machines must do what human operators instruct them to do.

## Contents

- [Context](#context)
- [Operating Systems](#operating-systems)
- [System Software](#system-software)
- [Firmware](#firmware)
- [Hardware](#hardware)
- [Resources](#resources)
- [Contributing](#contributing)
- [License](#license)

## Context

Emerging legislation in multiple jurisdictions is shifting the burden of demographic age verification from web applications down to the operating system layer. Laws such as California's AB 1043 and Brazil's ECA Digital mandate that operating systems collect, store, and expose user birth dates through standardized APIs, transforming what was previously a neutral execution environment into an active agent of identity classification, and converting computers in to machines that refuse to do what they are instructed by a human to do just because the human in charge does not belong to a certain demographic.

In the Linux ecosystem, this materialized when systemd merged [PR #40954](https://github.com/systemd/systemd/pull/40954), adding a `birthDate` field to its userdb JSON records. 

The projects listed here reject this paradigm. They maintain that computing infrastructure must remain demographic-neutral, treating users as entities authenticated solely by permissions, not biological age.

## Operating Systems

Operating systems whose developers or publishers have taken a public stance against implementing age verification, or have taken active measures to avoid compliance.

- [Ageless Linux](https://agelesslinux.org): A conversion script for Debian-based OS meant to be applied over a standard Debian 13 installation (or equivalent) that replaces OS identity metadata and deploys a stub age-verification API that deliberately returns an error and terminates. Designed strictly for "humans of indeterminate age." ([Statement](https://x.com/lundukejournal/status/2032951803134837237))
- [Omarchy Linux](https://omarchy.org/): Arch Linux and Hyprland-based development environment created by David Heinemeier Hansson (DHH). The developer publicly dismissed AB 1043 as unenforceable and stated there are no plans to respond to it. ([Statement](https://x.com/lundukejournal/status/2029580164498108846))
- [Artix Linux](https://artixlinux.org/): Rolling-release Arch-based distribution built entirely without systemd, using OpenRC, runit, or s6 as init systems. Issued the statement: "We'll NEVER require any verification or identification from the user." Architecturally immune to the userdb `birthDate` field since the init systems it ships have no centralized user metadata database. ([Statement](https://x.com/lundukejournal/status/2034776326901555488))
- [Devuan Linux](https://www.devuan.org/): Systemd-free fork of Debian with official developer statements confirming refusal to implement age tracking. ([Statement](https://x.com/lundukejournal/status/2034697759291310115))
- [GrapheneOS](https://grapheneos.org/): Privacy-hardened mobile OS based on AOSP (Android). Developers equated regional age mandates to authoritarian censorship, stating they are under no more obligation to filter the internet for California than for China. ([Statement](https://x.com/lundukejournal/status/2035073741613338964))
- [Adenix GNU/Linux](https://www.adenixgnulinux.org/): Debian-ecosystem distribution maintained by J. Mazzullo. Frames age mandates as First Amendment violations and has petitioned upstream Debian for root-level tools to purge and permanently blacklist state-mandated surveillance packages. ([Statement](https://lists.debian.org/debian-legal/2026/03/msg00022.html))
- [Vendefoul Wolf Linux](https://vendefoul-wolf-linux.sourceforge.io/index_en.html): Developer statements confirming refusal to implement age verification. ([Statement](https://x.com/lundukejournal/status/2035390136356077822), [#2](https://x.com/vendefoulwolf/status/2035441292520386852))
- [FreeDOS](https://freedos.org/): Open-source DOS-compatible OS. Project coordinators reject the imposition of demographic surveillance on legacy command-line architectures. ([Statement](https://x.com/lundukejournal/status/2034770975309361583))
- [Golden Dog Linux](https://goldendoglinux.org/): Lead developer Alexia Michelle stated the project will not implement age verification, citing adherence to open source standards. (Statement was published as an Instagram story and is no longer available; its existence was verified by [Protecció de la Frontera Electrònica](https://fronteraelectronica.cat).)
- [MX Linux](https://mxlinux.org/): Debian-based desktop distribution. The development team stated that no one on the team wants to implement age verification, citing concerns about user privacy, feasibility, and consistency with open source principles. ([Statement](https://linuxiac.com/mx-linux-takes-clear-stance-against-age-verification-requirements/))
- [EndeavourOS](https://endeavouros.com/): Arch-based distribution. The team stated they lack the infrastructure, manpower, or resources to implement age verification and that it goes against FOSS fundamentals. They also noted that no FOSS entity was represented when the law was created and called on the OSI, FSF, and Linux Foundation to act on behalf of distributions without US legal representation. ([Statement](https://endeavouros.com/news/whats-new-in-endeavouros-titan-release/))
- [Void Linux](https://voidlinux.org/): Independent distribution using runit as init system (systemd-free). A moderator posted a stickied comment on the official subreddit stating "we have no plans at this time" to implement age verification. ([Statement](https://www.reddit.com/r/voidlinux/comments/1ryhgpl/comment/obeigup/), [#2](https://x.com/LundukeJournal/status/2036521455752495439))
- [Garuda Linux](https://garudalinux.org/): Arch-based distribution. The team stated that Garuda Linux will not implement any age verification measures, since their legal jurisdictions have no laws mandating it. They also called on the community to direct its anger at politicians and lobbying organizations rather than at volunteer distribution developers. ([Statement](https://forum.garudalinux.org/t/a-statement-on-age-verification-the-state-of-the-community-discourse/47652))

These projects resist by obstructing and preemptively blocking access from jurisdictions with age verification laws or by revoking their software license for residents of those jurisdictions.

- [MidnightBSD](https://www.midnightbsd.org/): FreeBSD-derived desktop OS. Modified its COPYRIGHT file to explicitly revoke the software license for residents of jurisdictions requiring OS-level age verification: Brazil effective immediately, California effective January 1, 2027. ([License](https://github.com/MidnightBSD/src?tab=License-1-ov-file), [Statement](https://x.com/midnightbsd/status/2030992394703732872))
- [Arch Linux 32](https://archlinux32.org/): Community-driven 32-bit fork of Arch Linux. Implemented IP-level blocking of all Brazilian traffic and forbids usage in Brazil and California to avoid catastrophic fines. ([Statement](https://x.com/lundukejournal/status/2033896030178029675))

## System Software

Forks and patches that remove age-verification infrastructure from upstream codebases.

- [Liberated systemd](https://github.com/jeffrey-sardina/systemd): Fork of systemd maintained by Jeffrey Sardina that removes the `birthDate` field and all associated parsing, storage, and display code from userdb. Created after upstream systemd merged [PR #40954](https://github.com/systemd/systemd/pull/40954) adding the field, and the lead maintainer [closed a community revert attempt](https://github.com/systemd/systemd/pull/41179) without merging. Retains full code parity with upstream in all other respects.
- [systemd-no-age-verification](https://github.com/r4shsec/systemd-no-age-verification): Fork of systemd by cybersecurity researcher R4shSec that removes the age verification introduced via [PR #40978](https://github.com/systemd/systemd/pull/40978). ([Statement](https://r4shsec.github.io/posts/how_to_remove_systemd_age_verification/))
- [systemd-fuck-california](https://github.com/Queer-Coded-LGBTQ/systemd-fuck-california): Fork of systemd by [Queer Coded](https://queercoded.lgbt/) that removes age verification. Described as "systemd, but without age bs added in."
- [paramazo/systemd](https://github.com/paramazo/systemd): Fork of systemd by paramazo, the author of the upstream [revert PR #41179](https://github.com/systemd/systemd/pull/41179) that Poettering closed without merging. The revert argued that birth date storage creates a new class of sensitive user data, that community-driven distributions have no desire to act as identity authorities, and that precedent already exists for non-compliance over half-measures.
- [ganitam/systemd](https://github.com/ganitam/systemd): Fork of systemd taken just before the age verification addition, by [Ganitam](https://ganitam.in/) developer. The GitHub description expresses hope that more skilled developers and maintainers will do the same (i.e., encourages others to fork systemd to avoid its age restrictions).
- [GSYT-Productions/systemd-fork](https://github.com/GSYT-Productions/systemd-fork): Fork of systemd by [GSYT Productions](https://github.com/GSYT-Productions), the company behind BunnyPad. Described as "The systemd System and Service Manager, without the stupid Age Verification."
- [fightthesystemd](https://github.com/Pingasmaster/fightthesystemd): Fork of systemd by Adrian Noyes, defensive cybersecurity specialist. Described as "Systemd without the nonsense: no age verification, no lighthouse built-in."
- [systemd-saneagecheck](https://github.com/HaplessIdiot/systemd-saneagecheck): Fork of systemd by Collin (HaplessIdiot), a hobbyist developer on Steam Deck and OpenMandriva Linux. Described as "The systemd System and Service Manager with age verification bypass and polling rate options for said feature."
- [unshitted-systemd](https://github.com/Codiak540/unshitted-systemd): Fork of systemd by Codiak540. Described as "A fork of systemd aiming to make SystemD better. Sue me California."

## Firmware

- [DB48X](https://48calc.org/): Open-source calculator firmware whose developers openly rejected age tracking, underscoring the overreach of legislation broad enough to encompass non-general-purpose devices. ([Statement](https://github.com/c3d/db48x/blob/dev/LEGAL-NOTICE.md), [#2](https://x.com/lundukejournal/status/2027358439991615715))

## Hardware

- [Ageless Device](https://agelesslinux.org/hardware.html): A series of RISC-V-based computing devices (Milk-V Duo S, SG2000 SoC with 0.5 TOPS NPU) in three tiers ranging from $6 to $18, pre-flashed with Ageless Linux and labeled as AB 1043 noncompliant. Designed to be handed to children at STEM fairs, libraries, and maker events as an act of civil disobedience. Build instructions and hardware designs are released under the Unlicense.

## Resources

- [DoesItAgeVerify](https://github.com/BryanLunduke/DoesItAgeVerify): Maintained by Bryan Lunduke. A running list tracking the age verification compliance status of open-source operating systems. Covers projects planning to implement, projects refusing, and the current state of enacted and proposed legislation.

## Contributing

Contributions are very welcome. If you know of a FLOSS project that has taken a public stance against age verification, not necessarely at the OS-level, please open a pull request adding it to the appropriate section. Please kindly include a link to the developer statement or relevant source.

## License

[CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/)
