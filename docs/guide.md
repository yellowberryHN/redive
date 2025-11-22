---
title: The DiVER's Guide
---
# The DiVER's Guide

## What is this?

This document contains instructions for setting up a WACCA arcade cabinet with a thrown together OS while still
maintaining the functionality of the game. I've written this guide to be as beginner-friendly as I could, 
but it still requires a level of technical background, which you are assumed to have.

> DANGER: **Important!**
> The instructions on this page are intended **only for original hardware!** They are not recommended for non-cab setups.

> WARNING: **Disclaimer**
> This process takes a while (around 2-3 hours), there's a lot of tedious setup, and it's a bit of a pain in the ass.

> QUESTION: **"Do I need this guide?"**
> If you only intend to play on [popular network],
> **this guide is not for you, please follow the instructions provided by the network.**

> NOTE:
> The configuration here will set up your cab in a similar way to how the cab is normally set up.
> This isn't super future-proof and relies on old versions of software. There will *eventually* be a new guide,
> which will provide a way to run a more modern system and still run the game.

### Things you'll need

- [<ins>***Game files***</ins>](#archive "internet archive moment") (The guide was written for 3.07.01, but should work 
  with most versions)
  > FAILURE: **Unsupported versions**
  > As of July 2025, all versions of **SDHN or SDJE** (Chinese version) do not 
  > work with the configuration laid out in this guide. This may change in the future.
  > 
  > Please ensure you are working with clean game files if you run into issues.
- Phillips #2 screwdriver, and ideally JIS #2 as well.
- An empty SATA SSD with at least 128GB of capacity (I use [this one](https://www.amazon.com/-/dp/B08CK7T9FG/) in mine)
- [An ISO of **Windows 10 Enterprise LTSB 2016 x64**](https://drive.massgrave.dev/en_windows_10_enterprise_2016_ltsb_x64_dvd_9059483.iso)
  ([mirror](https://mega.nz/file/PBtggDaA#HySjX6zWohJKRVqpt_qUYgzRCBFzTmnNDXWESj_mvWI)) (This is important)
- A 16gb or higher capacity flash drive (Turn this drive into a bootable drive of the ISO above using
  [Rufus](https://rufus.ie/en/) or equivalent)
- Some sort of USB hub with at least 3 ports (technically optional, but annoying otherwise)
- A spare keyboard and mouse
- An external 1080p monitor that can swivel to portrait and has HDMI or DisplayPort input on it (not strictly required,
  but a huge pain in the ass if you don't have it)
- These files on the flash drive:
  - [7-Zip](https://7-zip.org)
  - [MAS](https://github.com/massgravel/Microsoft-Activation-Scripts)
    (It's annoying having your cab nag you to activate Windows)
  - [Motherboard Drivers](https://www.gigabyte.com/us/Enterprise/Embedded-Computing/MDH11BM-rev-10#Support):
      - Intel Management Engine 11.6.29.3287
      - Intel Chipset 10.1.1.38
      - Realtek Audio 435
  - Additional Drivers
      - [Nvidia Graphics Drivers](https://www.nvidia.com/en-us/drivers/details/141906/)
        (Older version, newer versions might work? Probably not.)
      - [FTDI D2XX USB to Serial](https://ftdichip.com/wp-content/uploads/2021/08/CDM212364_Setup.zip) ([mirror](files/CDM212364_Setup.zip))
  - [DirectX June 2010 Redistributable](https://www.microsoft.com/en-us/download/details.aspx?id=8109)
  - [Visual C++ 2012 Redistributable x64](https://www.microsoft.com/en-us/download/details.aspx?id=30679)
  - [Visual C++ 2015-2022 Redistributable x64](https://aka.ms/vs/17/release/vc_redist.x64.exe)
  - [TeamTofuShop's ST](https://gitea.tendokyu.moe/TeamTofuShop/segatools)
    ([Pre-built version, preconfigured](files/mercury-cab-2024-12-23.zip))

### Helpful things

- A computer capable of running Linux
- [Any USB 3.0 to SATA III adapter](https://www.amazon.com/-/dp/B00HJZJI84)
  (I use [this one](https://www.amazon.com/-/dp/B0B589LJXD/), but it's overkill for this)
- [Rii 2.4GHz wireless mini keyboard mouse combo](https://www.amazon.com/-/dp/B00Z81U3YY)
  (Useful to have in the event you don't want to deal with a wired mouse and keyboard)

----

## Part 0: ALLS Extraction and Drive Swap

### ALLS Extraction

> WARNING:
> **Ensure the cab's main power is disconnected, because it should be.** This may be obvious, but make sure.

We need to take the ALLS computer out so that we can install the new drive. 
Unfortunately it's quite difficult to open the ALLS while it's still in the cab, so we must remove it for now.

Inside the cab, you will find the ALLS firmly attached to the subwoofer. If your cab came with a keychip, you will
first want to remove it from the keychip slot by squeezing on the bottom of it and pulling it out. Don't misplace that.

Next, unplug the single connector inside to the right of the subwoofer and left of the coin box. Lastly, you want
to start by detaching all the cables from the ALLS and then undoing the 2-3 cable ties that are holding the cables
in place. The cable ties can be tricky; you want to pull upwards on the tab until it clears the hook and then feed it
through in reverse.

Now your ALLS should be free from cable hell. After moving the cables out of the way, locate the 2 screws
to the left and right of the subwoofer at the bottom and remove them. The entire subwoofer/ALLS assembly should now
slide directly outwards towards you and can be removed from the cab to be worked on.

The ALLS PC has **7** screws securing the top panel, 2 on the top, 3 in the front, 1 on the right side, and 1 on the
left side (that doesn't look attached). After removing those screws, you can slide the top panel forward and
lift it up and out.

### Drive Swap

You should now be presented with the drive cage at the top of the case. Removing the 2 screws located on either side of
the lip of the cage will allow the cage to be removed from the frame and the drive can then be unplugged from the SATA
connectors. There are an additional 4 screws holding the drive to the cage, remove those as well.

You now should have a drive in your possession that weighs more than it looks like it should.
At this point, I would ***heavily recommend***
[taking a full disk image of the drive **ON LINUX**](guide/alls-image.md),
just in case anything happens to it.
> DANGER: **Scary Red Text Zone** 
> <span style="color: red; font-size: .8rem;">
> ***Do not plug this into any PC running Windows, it will turn into a paperweight!***
> </span>

Now you can install the new drive into the cage. Plug the SATA connectors back in, but don't install the cage back onto
the frame, unless you aren't using the USB to SATA adapter to transfer files to your drive, in which case you can.

Leave the top panel off for now and slide the subwoofer/ALLS assembly back into the cab. Be aware that there is an
alignment tab in the back of the cab where the subwoofer slots in. Don't screw the subwoofer down yet, you have to be
able to remove it to put the top panel back on later.

There should be a helpful diagram sticker on the front of the ALLS that shows you where to plug all of the cables in,
take note of the tags on the cables that assign them different roles. Plug everything back in *except the monitor* as
shown by the diagram, and don't put the ties back on just yet. At this point, you can also reinsert the keychip.

**Don't forget to plug in the subwoofer connector again.**

It's finally time to do some actual installing.

----

## Part 1: BIOS Configuration, Installing Windows

### Initial Setup

Before we continue, you should grab your external monitor, ensure it's in a landscape position, and plug it into the
graphics card. You should also ensure that your USB hub is connected, with your keyboard and mouse ready. You should
also plug in your USB drive with **Windows 10 Enterprise LTSB 2016 x64** to the hub. 

***It is very important that you have the monitor plugged in before booting the system, or it will not be recognized.***

You'll want to also plug your cab back into power.

### BIOS Configuration

> NOTE:
> This step can be skipped if you do not plan on booting into USB drives after setting up your new drive. This is simply
> a "nice to have" and not required for things to work properly.
> 
> **If you choose to skip this, simply flip the power switch on and continue.**

From here, grab the keyboard, flip the main power switch located the inside of the cab
(not the ALLS one, ensure that always stays on), and spam the <kbd>Del</kbd> key until you are prompted for the
BIOS password, which is `iG4k8yDa`.

Once you have access to the BIOS, you'll want to head into the `Boot` section and change the first boot device to 
`USB Hard Drive` (the other USB ones didn't work for me) and the second boot device to the Hard Drive, 
as shown in the picture.

> DANGER: **Do not change anything else!** You risk wiping your TPM key and make it impossible to boot from the
> original drive if you do!

Save and exit with <kbd>F4</kbd> and select `Yes` when you are done. It should reboot and
put you into the Windows installer.

### Installing Windows

Start the installation, and if it asks you for a product key at any point, skip it. Next, it will ask you what kind of
Windows install you want; pick `Custom` and you should be presented with the partitioning screen.

You will want to create a new partition on Drive 0 that is the default size (the entire drive). It will notify you that
it's creating additional partitions to help with Windows, and then you can continue to the next step.

From here, it will install Windows, which should take about 5 minutes or so. Once Windows notifies you that the system
will be rebooted, remove your USB drive from the hub and wait for the system to restart. Windows is now installed on
your machine.

Once the system has restarted, it should prompt you to answer a few questions about configuration. The keyboard
configuration should be the same as your preferred keyboard. For the privacy settings, just turn everything off, you
don't need any of that. It should now ask you for a username. This doesn't really matter, I just made mine `WACCA`.
**Leave the password blank so that the system will automatically log in and press Next.**

Wait a few moments, and you should be presented with the Windows desktop. Ensure the files mentioned in the preface are 
your USB drive, and insert it back into the USB hub. You now want to run the 7-Zip installer, as many things will
require you to extract archives. Once you've done that, open 7-Zip, go to `Tools > Settings`, and change all the
extensions for your user to 7-Zip.

Next, you'll want to run the MAS script. To extract it from its archive, you'll want to use the password `1234`. After
you run it, you'll want to select KMS38 and then select the first option. This will prevent Windows from screaming at
you to activate it after a few days.

Now, we can move on to installing the drivers that are necessary for interfacing with the various hardware of the cab.

----

## Part 2: Prerequisites Installation, Set Up Serial Ports, Group Policy Changes

### Prerequisites Installation

Run the installer for the Nvidia Display Driver, making sure to only select `NVIDIA Graphics Driver`,
you don't need GeForce Experience, because that shit sucks. Select `Custom Install`, uncheck everything, then click `Next`.
Wait for this process to complete, you may see your screen flicker.

> NOTE:
> If any of the installers prompt you to restart, select `Restart Later.`

Install the FTDI driver, Management Engine, Chipset, and Audio drivers.

Now install the both Visual C++ Redists, and the DirectX Redist. Specify a path for the DirectX Redist (I usually use
`C:\DX`), and run `DXSETUP` from that folder to install.

### Serial Port Setup

Next, you should modify the buffer sizes for the COM ports on the ALLS. This is something that's done by the stock ALLS
system, and it didn't seem to make much of a difference with or without it, but you might as well change it just to be
sure. Press <kbd>Win</kbd> + <kbd>X</kbd>, and open Device Manager from the list that appears. Open the `Ports` section,
and do the following for COM ports 1-4:

* Right click, click Properties
* Click Port Settings
* Click Advanced...
* Ensure that the Recieve Buffer is set to 14, and the Transmit Buffer is set to 1
* Click OK to confirm

### Group Policy Changes

Next we will disable OneDrive and Windows Defender, as both of these are high memory background processes that will just
suck up processing power for no real reason, since this machine isn't a typical PC setup. To disable these components,
do the following:

* Press the Win key, type `group`, and open the entry that says `Edit group policy`.
* Navigate to `Local Computer Policy > Computer Configuration > Administrative Templates > Windows Components`,
  and select OneDrive.
* Double click on `Prevent the usage of OneDrive for file storage`
* Change it from `Not Configured` to `Enabled` and click OK.
* Navigate back to the Windows Components section, and select `Windows Defender`.
* Double-click on `Turn off Windows Defender` and set it to `Enabled` as well.

You should now reboot the machine **from the Start Menu** to make sure all the changes have saved correctly.
> WARNING: Do not power cycle the cab until after the computer has shut down, as the changes may not save correctly.

----

## Part 3: Screen Rotation, Audio Setup

Once the system has rebooted, right-click on the desktop, choose NVIDIA Control Panel.
Navigate to `Display > Rotate display`, and select either `Portrait` or `Portrait (flipped)`, depending on the direction
that your monitor rotates. If your monitor has a resolution greater that 1080p,
navigate to `Display > Change resolution` and change your resolution to 1080 x 1920.

Now, press the Windows key, type `real` and open the Realtek HD Audio Manager. Change the Speaker Configuration from 
Stereo to Quadraphonic, right-click on the pink jack, and select `Connector Retasking...`. In the window that appears,
choose `Rear Speaker Out` and disable the auto popup dialog. Press OK on both dialogs.

After that, shut down the system and flip the main cabinet power switch (by the test and service buttons). This is
mostly to make sure the file system changes are journaled correctly, as if they aren't, connecting the drive to another
computer will cause all files transferred to it afterward to disappear when the system is booted again.

## Part 4: Game Setup and Configuration

Detach the new drive from the system and connect it to your USB to SATA adapter, and then to your computer.

> DANGER: **Scary Red Text Zone** 
> <span style="color: red; font-size: .8rem;">
> ***Again, as a reminder, do not under any circumstance connect the <ins>original</ins> drive to a Windows computer!***
> </span>

Once you have connected the drive, create a `WACCA` folder on the root of the drive, and then inside of it create 
another folder called `Reverse` (or whatever version you're using).

> FAILURE: **Unsupported versions**
> As of July 2025, all versions of **SDHN or SDJE** (Chinese version) do not 
> work with the configuration laid out in this guide. This may change in the future.
> 
> Please ensure you are working with clean game files if you run into issues.
  
Copy the game files into the directory you created. There should be folders named `bin`, `pxbin` and `WindowsNoEditor`
in the folder, as well as a few files. Navigate to the `bin` folder, and extract the ST zip into this folder.

If you are configuring a version that is pre-Lily (WACCA or WACCA S), you need to open the `start.bat` file 
**with a text editor**, and change `Mercury-Win64-Shipping.exe` to `Mercury.exe`.

> ABSTRACT: **ST Note**
> If you are ***not*** using the provided ST build, you will need to make some changes to `segatools.ini`:
>
> - Change `enable` to 0 under the `[touch]` and `[elisabeth]` sections
> - Add `enable=0` under the `[io4]` section
> - Add an `[aime]` section at the bottom and add `enable=0` on that as well

**Eject the drive**, plug it back in to the cab, and power the cab on.
 
We need to make additional configuration changes, but the files haven't been created yet, so you have to launch the game.
Navigate to the folder you installed the game in, and launch it by running `start.bat`. A big W should appear, the game
should start, and the lights on the cab should light up. Both LED and Touch checks should be successful.
It should then hang on the Network check, at this point you should press <kbd>Alt</kbd>+<kbd>F4</kbd> to close the game.

Open the file explorer again, and navigate back to the `bin` folder. There should now be an `appdata` folder. Navigate
to `appdata\SDFE\Saved\Config\WindowsNoEditor`, right click on `Hardware.ini`, and click `Edit`. Add `OfflineMode=True`
under the `[/Script/Mercury.MercuryNetworkSettings]` section and save the file.

Start the game again, and note that the game now skips the network check and loads to the main menu successfully.
 
Press the test button to open the test menu. Use the volume buttons to navigate up and down, and the test button to
select. Navigate to `Device Test Menu > Test of Sound-Speaker`. Ensure the speakers are working by selecting
`Replay BGM Sample`, picking `LEFT + RIGHT`. Plug some headphones into the jack to ensure that you can hear something
from them as well.
It will be quiet, but you should hear something. Once you have finished testing that, select `Return`.
 
Navigate to `Test of Input Machine` and ensure all the panels light up as you touch them. Press test and service
buttons at the same time to return. Navigate to `Test of Output Machine`, select `Control Panel LED` and ensure it
lights up the front panel. Select `Aime Reader LED` and ensure that it also lights up. If it does not, consult the
troubleshooting guide.
 
Return back to the main test menu and navigate to `System Setting > Closing Time Setting`. Go down to 
`All Days of the Week` and change it until all the times on the page say `OFF`. Select `Apply Settings and Reboot`.
This will not actually reboot the system, it will only close the game.

**If you are setting up multiple versions, repeat these steps for each version you wish to include.**

Follow the setup instructions for the [WACCA Launcher](launcher.md) and then return here.

Finally, you need to configure the cab's display for this new setup. Close all the programs you have open, and then
reopen NVIDIA Control Panel and navigate to `Display > Rotate display`. Disconnect your monitor from the GPU and connect
the cab's DVI cable if you unplugged it. Press <kbd>Alt</kbd>+<kbd>Spacebar</kbd>, press <kbd>M</kbd>, and click and
drag the window to the part of the display you can see. Rotate the display to `Portrait (flipped)` and press Apply.

Reboot the system and the game should now start automatically. Congratulations, you've now set up your cab!

## Part 5: Reassembly

Reassembly of the cab is quite simple. Ensure the power is off, unplug all the cables from the ALLS, including the cable
to the right of the subwoofer.

Pull the subwoofer-ALLS assembly out of the cab, secure the new drive to the drive cage, the drive cage to the top frame,
and put the lid of the ALLS back on (it's a little tricky, there's a lip on the left side that's not immediately obvious).

Screw in all 7 screws from the lid, then slide the subwoofer-ALLS assembly back into the cab, making sure to line up the
tab in the back, like before. Connect the subwoofer cable, and reconnect the ALLS cables, as done previously.

Screw in the two subwoofer screws at the bottom of the subwoofer assembly.

Optionally, you can put the cable ties back, for a cleaner look. You don't have to install them as they were before, you
can just run the tie through the hole, and it should hold itself in well enough.

Store the original drive somewhere safe, I personally keep mine in the bag that my manuals came in, but that's not an
option for everyone. You could also store it in the coin drawer, if you don't plan on using coins in your cab.
