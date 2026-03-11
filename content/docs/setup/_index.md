---
weight: 200
title: Setting up Fedora
---

# Setting up Fedora

## Before you begin

This guide focuses on streaming, so it will only lightly cover general Fedora concepts! For more in-depth documentation, visit the official [Fedora Documentation](https://docs.fedoraproject.org/) site.

This page will walk you through the general install and how to install important system software to get your system ready for multimedia and streaming.

You will need a USB drive of 4G or higher capacity to install Fedora.

> [!WARNING]
> All contents of the USB drive will be erased, so make sure there's nothing important on it!

## Installation

From the [Fedora KDE Plasma Desktop](https://fedoraproject.org/kde/) page, click on the download button to go to the downloads page. If you already know what you're doing, you can download an ISO image and boot it here.

Otherwise, scroll down to the Fedora Media Writer section, and choose the download appropriate for your current OS. Then, simply open Fedora Media Writer and follow the instructions. Let it **Download automatically**, and when prompted for the Fedora release to use, choose **Official Editions** and **Fedora KDE Plasma Desktop** and leave the version at the default (the latest stable version).

Reboot your computer with the USB device plugged in to boot into Fedora KDE (you might need to go into your UEFI setup screen and explicitly choose the USB drive as a boot device for it to work).

> [!TIP]
> While you're visiting your UEFI setup / BIOS, you might want to disable Secure Boot if you don't need it for Windows. This will make your life easier later, especially if you need to install the NVidia drivers.

The image you downloaded is a "Live" image, which will directly boot into a Fedora KDE environment where you can explore and see how the OS works before installing it (any changes you make and any files you save won't persist). Click the big install button to begin the installation, and follow the prompts which should be self-explanatory. Pay particular attention to the question about storage, as you can choose to overwrite an entire HDD/SSD drive or instead resize an existing OS to make space and have both installed at the same time (dual-boot).

You will be prompted to create a user and password. Don't forget it!

## First steps

The KDE first-time welcome screen will ask you a few questions. You can skip this if you want, but it's useful information. One of the steps will ask you whether you want to **Enable Third Party Repositories**. You can safely skip this, since you will be enabling more comprehensive software sources yourself later.

{{< image src="extra-repos-prompt.png" alt="Extra repositories dialog" >}}

If you are using WiFi, connect to the network by clicking the network icon in the system tray, choosing your network, and entering the password. If you are using wired Ethernet, you should already be connected automatically.

You will probably get a prompt titled **KDE Wallet Service** asking you to create a new wallet. You can choose **Classic, blowfish encrypted file** for the easiest option. Your Wallet is where the system stores saved passwords (similar to the macOS Keychain), including your WiFi password, which is why it's popping up now. During wallet setup, it might ask you to enter a new password for the wallet. You can use your login password here, which will allow the wallet to automatically unlock when you log in to the system, so you don't have to type two separate passwords.

{{< image src="kwallet-prompt.png" alt="KDE Wallet Service dialog" >}}

Now is a good time to update your OS, since the installation image will have somewhat out of date software. You might be prompted by a notification automatically. Otherwise, click on the start menu on the bottom left {{< icon src="images/fedora-logo-sprite.svg" >}}, and open up **Discover**. This tool is the graphical interface to install and update software. Click on **Updates** on the left, and click on **Update All** to begin downloading updates. You will be prompted to restart to complete the installation.

{{< image src="discover.png" alt="Discover app" >}}

> [!NOTE]
> Although Linux has a reputation for "not needing reboots" to install updates, and it is technically possible to update without a reboot, this is often clunky. You might find that applications stop working properly until a reboot, as the running and installed version of different system components conflict in strange ways. It's always best to use Discover to install updates with a full reboot cycle, especially if any system components are being updated.

## Setting up third-party software sources

Fedora is a somewhat conservative Linux distribution, and for legal and licensing reasons, it's missing some software that you will probably consider essential. Let's set things up so you have more software available.

> [!NOTE]
> You can blame [software patents](https://threadreaderapp.com/thread/1575885891922690048.html) for a lot of this mess.

### RPM Fusion

[RPM Fusion](https://rpmfusion.org/) is essentially "the parts of Fedora that cannot be called Fedora". You will need some of this software for proper multimedia support, and it is practically essential for streaming. In practice, these packages are maintained by some of the same people that maintain Fedora and to similar standards. This also includes packages for things like Steam.

We're going to set this up using the terminal. From the start menu, open **Konsole**. Then, copy and paste these commands one by one to set up RPM Fusion. Make sure to copy each command on its own, then press **Enter** and follow the prompts until you get back at the green `username@fedora:~$` prompt.

{{< image src="konsole.png" alt="Konsole" >}}

> [!TIP]
> Use Ctrl+Shift+V to paste in the terminal. Head over to the [Concepts](/docs/concepts#command-line-terminal) page to learn more about how to use the terminal.

Enable the "Free" repository (applications and software that is open source, but cannot be part of Fedora due to patent reasons, such as video codecs):

    sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm

Enable the "Nonfree" repository (applications that are not open source, such as Steam):

    sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

Now let's do an extra step to install some basic metadata for these repositories and also accept some prompts. After typing the next command, you will see one or several prompts that start with `Importing OpenPGP key` and ask you `Is this ok [y/N]:`. Type `y` and press Enter to accept.

    sudo dnf group upgrade core

> [!TIP]
> After doing the above, you can enable/disable RPM Fusion repositories directly in the **Discover** app, under **Settings**. You will also find repositories labeled "Steam" and "NVIDIA Driver". You don't need to enable those, they are just a subset of the "Nonfree" repository you enabled above that comes with Fedora for convenience.

### Flathub

Flathub is the primary repository of Flatpak software, which is used to package applications in a universal format across different Linux distributions.

> [!TIP]
> Check the [Concepts](/docs/concepts#packages-and-package-managers) page to learn more about Flatpak, and whether you should use the Flatpak or Fedora version of available software.

To enable Flathub, open the **Discover** app and click on **Settings** on the left. Then, enable the **Flathub** repository by clicking on the check box. Quit and reopen **Discover** to see the newly available software.

> [!TIP]
> You might also want to disable the **Fedora Flatpaks** source. These are Flatpaks built by Fedora, similar to native Fedora packages. This is mostly useful for users of immutable distros, like Bazzite and Fedora Silverblue. If you aren't using those, it will probably just be more confusing, since practically everything available on Fedora Flatpaks should be available as a native package too.

## Important system software

Now that you have enabled RPM Fusion, let's install some codecs that will make your life a lot easier.

    sudo dnf install libavcodec-freeworld

    sudo dnf update @multimedia --setopt="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin

> [!TIP]
> See the [RPM Fusion documentation page](https://rpmfusion.org/Howto/Multimedia) for more information.

## Drivers

In general, Fedora Linux ships with drivers for most of your hardware out of the box. However, there are two things you might need to install manually: **Hardware video decoding/encoding drivers** (due to the software patent mess), and the **NVidia GPU drivers** (for Nvidia GPU users). Choose the section appropriate for your GPU.

> [!TIP]
> For more information, see the  [RPM Fusion](https://rpmfusion.org/Howto/Multimedia) documentation and the [Fedora Project](https://fedoraproject.org/wiki/Hardware_Video_Acceleration) documentation on this subject.

### Intel CPUs with graphics and discrete GPUs

Install support for hardware encoding/decoding using these commands.

For newer CPUs starting with **Broadwell** ([list](https://github.com/intel/media-driver/#supported-platforms)):

    sudo dnf install intel-media-driver

For older CPUs:

    sudo dnf install libva-intel-driver

If you plan to use Steam or any Windows software, you'll also want the 32-bit version (choose the appropriate one):

    sudo dnf install intel-media-driver.i686

Or:

    sudo dnf install libva-intel-driver.i686

> [!NOTE]
> You can also install these graphically from the **Discover** app by searching for **Intel video**. They are called **The Intel Media Driver for VAAPI** (newer CPUs) and **HW video decode support for Intel integrated graphics** (older CPUs). However, that won't give you the option to install the 32-bit libraries if you need them.

### AMD GPUs and APUs

Install support for hardware encoding/decoding using this command:

    sudo dnf swap mesa-va-drivers mesa-va-drivers-freeworld

If you plan to use Steam or any Windows software, you'll also want the 32-bit version:

    sudo dnf swap mesa-va-drivers.i686 mesa-va-drivers-freeworld.i686

### NVidia GPU drivers

Fedora Linux ships with the open-source Nouveau/NVK drivers. These drivers are recommended for day to day tasks and actually integrate better with Linux in many cases, including tasks related to streaming! However, they might not provide the best compatibility/performance, and they also do not support hardware encoding.

> [!WARNING]
> If your system has hybrid graphics (e.g. an Intel or AMD CPU with integrated graphics) alongside NVidia, I highly recommend disabling them in your UEFI setup (BIOS) and using the NVidia card exclusively, if possible, unless you really know what you're doing. Hybrid graphics can be quite confusing as you might have to manually select which GPU is used by individual apps, and it also works particularly poorly with the NVidia proprietary drivers due to various bugs and missing features in those drivers.

> [!TIP]
> This is a quick overview for the most common case. Check the [RPM Fusion NVIDIA](https://rpmfusion.org/Howto/NVIDIA) page for more detailed information and steps.

You will need a **2014 or newer** GPU (Nvidia Maxwell or newer). If you have an older GPU, you should stick to the open source Nouveau drivers, as the proprietary drivers no longer support these GPUs (and you will run into a world of pain if you try to use older drivers, since they won't support modern Linux features).

If you have Turing or newer GPU (Geforce GTX 16xx or any RTX):

    sudo dnf install akmod-nvidia

If you have an older Maxwell through Volta GPU (Geforce GT/GTX 7xx through 1xxx or Titan V), then the last supported version of the NVidia driver is 580. At the time of this writing, this is just `akmod-nvidia`, but it will be split `akmod-nvidia-580xx` very soon. Try installing that one first:

    sudo dnf install akmod-nvidia-580xx

If that is not available, then proceed with `akmod-nvidia`, and keep in mind that you might have to manually switch to the `580xx` package in the near future:

    sudo dnf install akmod-nvidia

Finally, for 32-bit software support like Steam and Windows apps, add the 32-bit version of the CUDA/NVENC libraries as appropriate:

    sudo dnf install xorg-x11-drv-nvidia-cuda-libs.i686

Or:

    sudo dnf install xorg-x11-drv-nvidia-580xx-cuda-libs.i686

Reboot to switch to the newly installed drivers.

> [!NOTE]
> You can also install these graphically from the **Discover** app by searching for **NVIDIA**. However, that won't give you the option to install the 32-bit libraries if you need them.
