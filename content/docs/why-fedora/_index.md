---
weight: 100
title: "Why Fedora?"
---

# Why Fedora?

[{{< image src="Fedora_logo.svg" alt="Fedora logo" width="50%" zoom="0">}}](https://fedoraproject.org)

There is a huge variety of Linux distributions, so why choose Fedora if you're a streamer? Well, because I'm a package maintainer myself of course, so I can help make *your* streaming experience on Fedora better!

Okay, but why Fedora to begin with? In my opinion, Fedora strikes a great balance between being easy to use and newcomer-friendly, stability, and being up to date with the latest software. In particular, Fedora has a 6-month release cycle with a fairly open policy about updates between releases, which means you will not be left behind on software updates for long, while also making sure updates are tested and rolled out with time to catch bugs and issues. Fedora is neither a rolling distribution that *immediately* packages all software (which usually means less stability), nor is it a long-term-support distribution with a 2-year or longer release cycle (which means you will be left behind on new features and bugfixes), but rather strikes a great balance between the two.

The Fedora project supports the last two releases, which means that you can hold off updating to the latest Fedora release for up to half a year and still get security (and some software) updates. As a streamer, if you're concerned about stability, you can wait for two or three months after a release before upgrading, to make sure that any teething pains from updating a lot of software all at once are sorted out. Or you can choose to jump on the latest and greatest as soon as it's released (or even during the beta period before release), and get the latest and greatest software early and help test and make sure everything is working right. The choice is yours!

> [!NOTE]
> This site is not affiliated with or endorsed by the Fedora Project.

## What desktop environment should I use?

There are many desktop environments available for Linux. For streaming, and especially new users I highly recommend KDE Plasma. This desktop has many power user features that will make your life easier as a streamer, while having the overall base look and feel of a classic Windows environment, so you won't feel lost. KDE Plasma lets you customize all sorts of details about your desktop *without* requiring you to edit configuration files manually or learn any programming languages, so it is a great choice even if you are a newcomer or not a very technical person. KDE Plasma also has some of the best integration with newer desktop technologies like Wayland, and that means you won't run into many problems that often affect streamers on Linux (such as issues with OBS hotkeys or window/screen capture).

Where relevant, this guide will focus on using KDE Plasma, although everything that isn't related to the desktop itself will apply to most other desktop environments too.

> [!TIP]
> KDE Plasma is also the native Linux desktop available on the Steam Deck, so if you have one of those and you've ever gone into desktop mode, you already know what it looks like!

## Fedora derivatives

Fedora is one of the "major" base Linux distributions, and there are many derivative distributions based on Fedora. There are a couple that you might be interested in.

* [**Nobara**](https://nobaraproject.org) is a Fedora spinoff focused on gaming. It is essentially Fedora pre-configured for gaming and streaming, with extra packages on top. This means it is easier to set up, but also a bit less stable than baseline Fedora. Nobara does not exactly follow the Fedora release cycle but rather is a "pseudo-rolling" distribution that follows Fedora releases as they come, so essentially, it requires that you update to the latest release to continue getting updates (and does so automatically as part of regular system updates). Most of what I describe in this guide will work on Nobara too, but you can skip sections related to graphics driver and codec setup, as those things are pre-configured in Nobara for you. As above, I recommend choosing the **KDE Plasma** version if you go with Nobara.

* [**Bazzite**](https://bazzite.gg) is another spinoff focused on gaming, but this is based on Fedora Silverblue, which is an *immutable OS*. An immutable OS is kind of like macOS, where the OS itself cannot be modified by you, and you can only install applications on top. Instead of updates coming in as packages, the entire OS is updated in one go. This makes it more robust than a traditional Linux distribution, but also less flexible. Since Bazzite is immutable, you cannot use DNF/RPM to manage system or native packages. Instead, you should prefer Flatpak (described later) to install applications (there are [other ways](https://docs.bazzite.gg/Installing_and_Managing_Software/rpm-ostree/) to use RPM packages, but they are not recommended). If you use Bazzite, the portions of this guide about configuration and usage should still work for you, but the portions describing how to install software will be different. As with Nobara, drivers and codecs should be mostly handled for you.

This guide will focus on the official Fedora distribution, and in particular the KDE Plasma version.

## Contributing to Fedora

Fedora is also a volunteer-driven distribution, and that means anyone (like me, or you!) can contribute. As a user, one of the easiest and best ways to contribute is to watch the [Fedora Updates](https://bodhi.fedoraproject.org) site for updates for software that you care about, and beta test updates before they go live. If you catch a problem, you can report it directly on the site, and that will prevent the update from going through until it is fixed. Meanwhile, you can easily downgrade to the stable version in the meantime.

You can also report bugs in the [Bugzilla](https://bugzilla.redhat.com). Choose the correct category and package app, and they will be directly routed to the package maintainers. If an app crashes, Fedora automatically gives you a notification and allows you to file the crash as a bug with debugging information, directly from your desktop.

If you find a bug in a Fedora package and you want to help fix it, all you have to do is fork the package in the [Fedora Package Sources](https://src.fedoraproject.org) site, and submit a PR. There are already multiple volunteers besides myself focused on streaming (and the larger [Multimedia SIG](https://fedoraproject.org/wiki/Category:Multimedia_SIG)), and we're always happy to get more people on board.
