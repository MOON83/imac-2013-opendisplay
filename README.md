# Turn Your Late 2013 iMac into a Monitor for a Modern Mac
## A Free, Beginner-Friendly Installation Guide

**No Linux experience required. No programming. No Docker. No need to open or modify your iMac.**

Do you have a beautiful old 27-inch iMac sitting around that you would love to use as an external monitor for your newer MacBook or Mac mini?

That's exactly what I wanted to do.

After plenty of experimentation, I successfully converted my Late 2013 iMac into a working external display for my Apple Silicon MacBook Air at its full **2560 × 1440 resolution**.

I've now made the modified Linux operating system available for others to try.

This guide explains how to get started, even if you've never done anything remotely technical before.

**A quick note:** This is an experimental community release. The configuration works on my particular iMac, but the downloadable image itself has not yet been independently boot-tested, and other hardware configurations may behave differently.

---

## 1. What You Need

You will need:

- **A Late 2013 27-inch iMac.** Mine has an NVIDIA GeForce GT 755M graphics card. Other models may work, but have not yet been confirmed.
- **A modern MacBook or Mac mini.** I used an Apple Silicon MacBook Air running a recent version of macOS.
- **An SD card or USB memory stick, preferably 8 GB or larger.** This will hold the special operating system.
- **An Ethernet cable.** This connects the two computers directly.
- **An Ethernet adapter**, if your modern Mac doesn't have an Ethernet socket. A USB-C-to-Ethernet adapter is fine.
- **A keyboard connected to the iMac**, preferably a wired one, for selecting the startup drive.
- **An internet connection** on your modern Mac to download the necessary files.

You do **not** need to buy an expensive display conversion board, install Windows, or remove anything from inside your iMac.

You also do not need to erase or replace macOS on the iMac.

## 2. Download the Ready-Made Operating System

I've already done the difficult work of preparing Debian Linux with the appropriate NVIDIA graphics support and OpenDisplay software.

You only need to download the finished image.

**Download it here:**

https://github.com/MOON83/imac-2013-opendisplay/releases/tag/v0.1.0-rc1

Open that page, find the section labelled **Assets**, and download:

`iMac_2013_OpenDisplay_GITHUB.dmg`

The download is approximately 2.15 GB.

This file contains the special Linux system that will allow the iMac to receive a picture from your modern Mac.

**Important:** You do not need to open the DMG file, install Linux manually, or copy its contents into a folder.

Instead, we're going to write the complete image onto your SD card or USB stick.

## 3. Put the Operating System onto Your SD Card or USB Stick

This is probably the most unfamiliar part, but it's quite straightforward.

We need a little free application that can write an entire operating-system image onto a removable drive.

It's called **balenaEtcher**.

Download it here:

https://etcher.balena.io/

Install and open balenaEtcher on your Mac or Windows computer.

Now follow these steps:

**Step A — Insert your SD card or USB stick.**

Make sure it doesn't contain anything you want to keep. The next process will erase everything on that selected card or stick.

**Step B — Click “Flash from file”.**

Find and select the image you downloaded:

`iMac_2013_OpenDisplay_GITHUB.dmg`

**Step C — Click “Select target”.**

Choose your SD card or USB stick.

**Be very careful here!** Double-check that you've selected the removable drive, not an external hard drive containing important files.

**Step D — Click “Flash!”**

The application will write the Linux operating system to your selected drive.

Allow the process to complete and, if available, finish its verification stage.

If balenaEtcher refuses to open the DMG or reports an image-format error, stop and report the message rather than renaming the file or trying to copy its contents manually.

When finished, safely eject the SD card or USB stick.

You now have your iMac display operating system ready to boot!

## 4. Start Your Old iMac Using the New Operating System

Now move over to your old iMac.

1. Shut down the iMac completely.
2. Insert the newly prepared SD card or USB stick into the iMac.
3. Connect your keyboard.
4. Switch the iMac on while holding the **Option (⌥)** key. If using a Windows keyboard, hold **Alt**.
5. A startup selection screen should appear.
6. Select the option labelled **EFI Boot** and press Enter.

Your iMac should now begin loading Linux from the removable drive.

You may see some technical messages or a startup menu. This is normal.

The image is configured to launch the OpenDisplay receiver automatically. It also includes diagnostic options in case something goes wrong.

**Very important:** You are not installing Linux onto the iMac's internal hard drive. You are simply starting a separate operating system from the SD card or USB stick.

Your original macOS installation remains untouched.

The iMac is now being prepared to receive a picture from your modern Mac.

## 5. Connect the Two Computers

Take your Ethernet cable and connect:

**Your modern MacBook or Mac mini → Your old iMac**

If your modern Mac doesn't have an Ethernet socket, use a USB-C-to-Ethernet adapter.

This is a direct connection. You don't need a router or network switch between the computers.

The system uses Ethernet to transmit the picture from your modern Mac to the iMac.

### A small but important network setting

The Linux system on the iMac is configured to use this network address:

`10.10.10.2`

Your modern Mac needs to use:

`10.10.10.1`

On the modern Mac:

1. Open **System Settings**.
2. Select **Network**.
3. Choose the Ethernet connection attached to the iMac.
4. Open **Details**, then **TCP/IP**.
5. Set **Configure IPv4** to **Manually**.
6. Enter the following:

**IP Address:** `10.10.10.1`

**Subnet Mask:** `255.255.255.0`

**Router:** Leave blank.

Click OK or Apply to save the settings.

If your Mac has several network connections, make sure you're changing the Ethernet adapter connected to the iMac, not your normal Wi-Fi connection.

Your Wi-Fi can remain connected to the internet as usual.

## 6. Install OpenDisplay on Your Modern Mac

The old iMac already has the receiving software installed inside our Linux image.

Now your modern Mac needs an application to send its picture.

That application is called **OpenDisplay**.

You can download it for free here:

https://opendisplay.app/

Look for the **macOS Sender** download.

OpenDisplay currently requires macOS 14 or later for the Mac sender.

Install the application on your modern Mac and open it.

If macOS asks for permissions, follow the prompts. In particular, OpenDisplay needs permission to record the virtual display that it sends to your iMac.

You can check this under:

**System Settings → Privacy & Security → Screen & System Audio Recording**

Depending on your macOS version and which features you use, it may also ask for Local Network or Accessibility permission.

These permissions allow the software to transmit the display and interact with the receiving device.

## 7. Connect to Your iMac

Now for the exciting part!

Make sure:

- The iMac is switched on and has booted from the Linux SD card or USB stick.
- The Ethernet cable is connected between the computers.
- OpenDisplay is running on the modern Mac.
- The modern Mac's Ethernet connection has been configured as described above.

Open OpenDisplay on your MacBook or Mac mini.

Look for the available receiver named:

**`imac27`**

Select it to connect.

If the connection succeeds, your iMac should begin displaying a second desktop from your modern Mac.

You can now move your mouse and drag windows across to the iMac, just as you would with another external monitor.

On your modern Mac, open:

**System Settings → Displays**

You should see the additional display.

Use the Arrange option to position it to the left or right of your main screen, whichever matches your physical setup.

Congratulations! Your old iMac is now functioning as an external monitor.

## 8. Getting the Full 2560 × 1440 Resolution

This part is especially important.

The original OpenDisplay project used a lower streaming resolution, which made the picture look slightly soft on the 27-inch screen.

Our adapted image is already configured for the iMac's native resolution:

**2560 × 1440**

You shouldn't need to change anything.

If you ever need to inspect the setting, the configuration file is called:

`od-kiosk.conf`

It is located on the removable drive's **DEBLIVE** partition.

The relevant settings are:

```ini
OD_WIDTH=2560
OD_HEIGHT=1440
OD_DECODER=avdec_h264
OD_ARGS=--no-gl
```

Leave these as they are unless you're deliberately troubleshooting or experimenting.

You can also inspect the available resolutions in your modern Mac's **System Settings → Displays**.

One small limitation: transmitting a full 2560 × 1440 image requires more processing power than using a lower resolution, so you may notice some latency or a reduced frame rate.

This is a network-streamed display, not a direct physical video connection.

For writing, browsing, research and ordinary desktop work, it may be a perfectly useful solution.

## 9. What If Something Doesn't Work?

Don't panic! I encountered quite a few problems while getting mine working.

Here are some useful starting points.

**The iMac doesn't show “EFI Boot”.**

Check that the removable drive was flashed properly, rather than having files copied onto it normally. Make sure it's inserted before starting the iMac, and try holding Option or Alt from the moment you switch it on.

**Linux starts, but the screen stays black.**

The system includes diagnostic boot options. If necessary, restart and enter the GRUB startup menu. You can press Esc to reveal it if it is hidden.

Choose a diagnostic option with the OpenDisplay kiosk disabled, and photograph any messages that appear.

If Linux reaches a text prompt, that's useful information: the operating system has started, even if the graphical receiver hasn't.

**OpenDisplay can't find the iMac.**

Check the Ethernet cable and make sure the modern Mac's Ethernet address is set to `10.10.10.1`, with subnet mask `255.255.255.0`.

The iMac should be at `10.10.10.2`.

Also check OpenDisplay's macOS permissions.

**The picture isn't sharp.**

Check that the receiver configuration says `2560 × 1440`, and inspect the resolution selected in macOS Display settings.

**The picture is slow or occasionally freezes.**

Try reconnecting OpenDisplay. Higher resolutions can require more CPU power and may reduce the frame rate. The original project also documents a lower 2048 × 1152 mode that may perform better on some hardware.

**The SD card or USB stick seems unreadable in macOS.**

This can happen because the operating system uses Linux-specific data structures. Don't erase or reformat the drive if it's working in the iMac.

## 10. Need More Help? Ask ChatGPT

This entire conversion was achieved by someone with no previous experience of Linux, bootloaders, graphics drivers or programming, working step by step with ChatGPT.

If you get stuck, you can try the same approach.

Open ChatGPT and share these two links:

**Original project:**

https://github.com/tlscodes/imac-as-monitor

**Our successful 2013 iMac adaptation:**

https://github.com/tlscodes/imac-as-monitor/issues/2

You can then write something like:

> I'm trying to use my Late 2013 27-inch iMac as a monitor for my modern Mac. I'm following this OpenDisplay Linux guide, but I've encountered a problem. Please read the project information and help me troubleshoot it one step at a time. I'm not technically experienced, so give me simple instructions and explain exactly what to do.

You can also upload screenshots or photographs of error messages and copy Terminal output directly into the conversation.

AI assistance isn't guaranteed to be correct, particularly with commands that modify disks, so always check instructions carefully and back up important files.

But having someone guide you through the process, step by step, can make an enormous difference.

## 11. Important Compatibility Information

This configuration has been successfully used with:

**iMac:** Late 2013, 27-inch, NVIDIA GeForce GT 755M  
**Operating System:** Debian 13 Linux  
**Graphics Driver:** Nouveau  
**Display Resolution:** 2560 × 1440  
**Source Computer:** Apple Silicon MacBook Air  
**Connection:** Direct Ethernet cable  
**Streaming Software:** OpenDisplay

This particular combination has been demonstrated on working hardware.

Other 2013 iMac graphics cards, including the GTX 775M and GTX 780M, have not yet been verified with this release.

The packaged download is currently labelled a **release candidate** because it has passed disk-image integrity verification but has not yet been boot-tested independently.

This is also not Apple's original Target Display Mode. It works by starting Linux on the iMac and streaming the modern Mac's picture over Ethernet. The stream is not encrypted, so the connection should be used only on a trusted network, ideally the direct Ethernet cable described here.

## 12. Credits and Thanks

This adaptation would not have been possible without the original open-source project created by **tlscodes**:

https://github.com/tlscodes/imac-as-monitor

And the developers of **OpenDisplay**:

https://opendisplay.app/

The Debian Linux, Nouveau, GRUB and other free-software communities also provide the underlying technology.

Our contribution was testing and adapting the Linux receiver configuration for the Late 2013 iMac with NVIDIA graphics, with extensive assistance from ChatGPT.

I'm sharing this because I know how frustrating it is to have a beautiful old computer with a perfectly good screen that seems impossible to use with modern equipment.

Hopefully this guide helps someone else give theirs a second life.

**Enjoy your rescued iMac!**

---

**Release:** https://github.com/MOON83/imac-2013-opendisplay/releases/tag/v0.1.0-rc1

**Full technical report:** https://github.com/tlscodes/imac-as-monitor/issues/2

**Status:** Experimental community release, November 2026.

## Bonus: Make Your iMac Start Automatically Without a Keyboard

Once everything is working, there's one final improvement that makes the whole setup much more convenient.

**You can configure the iMac to boot directly into OpenDisplay whenever you switch it on. No holding Alt, no selecting EFI Boot, and no navigating Linux menus!**

There are two separate startup settings to configure. You only need a keyboard for the initial setup.

### Step 1 — Make the iMac Remember the Linux SD Card

1. Leave your working Linux SD card or USB stick connected to the iMac.
2. Restart the iMac while holding **Option (⌥)** on an Apple keyboard, or **Alt** on a Windows keyboard.
3. When Apple's startup selection screen appears, highlight **EFI Boot**.
4. Hold down the **Control (Ctrl)** key.
5. While holding Control, press **Enter** to boot.

On compatible Intel Macs, this tells Apple's startup system to remember that drive as the preferred startup device.

On our Late 2013 iMac, the machine subsequently started directly from the Linux SD card without needing to hold Alt again.

If this doesn't work on your machine, you may still need to select EFI Boot manually. The startup preference can also be reset.

### Step 2 — Make Linux Start OpenDisplay Automatically

The second step removes the need to select OpenDisplay manually from the Linux startup menu.

Shut down the iMac, remove the Linux SD card or USB stick, and connect it to your modern Mac.

Open the drive named **DEBLIVE**.

Inside it, locate:

`boot/grub/grub.cfg`

This small configuration file controls the Linux startup menu.

**Make a backup copy of `grub.cfg` before editing it.**

Open the original file using TextEdit, making sure you're editing it as plain text.

Near the top, find the lines beginning with `set timeout`, `set timeout_style`, and `set default`.

Change those settings to:

```text
set timeout=3
set timeout_style=menu
set default=od
```

Leave everything else unchanged.

Here's what these settings mean:

- **`timeout=3`** — Linux waits just three seconds.
- **`timeout_style=menu`** — The startup menu remains visible for troubleshooting.
- **`default=od`** — OpenDisplay starts automatically.

Save the file, keeping its original name `grub.cfg`, without adding `.txt`.

Safely eject the SD card or USB stick and return it to the iMac.

### Step 3 — Enjoy Automatic Startup!

Switch on the iMac normally.

If both startup settings have been accepted, the computer should:

1. Automatically find the Linux boot drive.
2. Start Linux without requiring any keyboard input.
3. Select OpenDisplay after three seconds.
4. Launch the receiver, ready for your modern Mac to connect.

**That's it! Your old iMac now behaves much more like a dedicated external monitor.**

You can even disconnect the keyboard from the iMac for everyday use.

The Linux diagnostic options remain available through the startup menu if you ever need to troubleshoot.

**Test both changes before disconnecting your keyboard.** This procedure worked on our Late 2013 iMac, but automatic EFI startup selection may behave differently on other machines.

And remember to leave the Linux SD card or USB stick connected whenever you want to use the iMac as a monitor!
