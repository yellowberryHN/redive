---
title: WACCA Launcher
---
# WACCA Launcher

WACCA Launcher is a tool that automatically launches the game for you
at startup, and also allows you to run multiple versions of WACCA on your cab and switch between them easily.

## Prerequisites

- Game files, set up with Hay1tsme's ST
- [The latest version of WACCA Launcher](https://github.com/YellowberryHN/WACCALauncher/releases/latest)
- Keyboard and mouse plugged into the cab

## Setup

NOTE: This guide assumes you already have your cab set up in a similar way to how is described in [the DiVER's Guide](guide.md).

Extract the `WACCALauncher.zip` into a folder outside your game files.
I personally have my folder structure set up like this:

```text
C:\
└─ WACCA\
   ├─ Offline\
   │  └─ ...
   ├─ Reverse\
   │  └─ ...
   ├─ Lily R\
   │  └─ ...
   ├─ Lily\
   │  └─ ...
   ├─ WACCA S\
   │  └─ ...
   ├─ WACCA\
   │  └─ ...
   └─ <launcher files>
```

There should be a file called `wacca.ini`, you'll want to edit that file to point to the paths of your WACCA game files.
Here's what mine looks like

```ini
[general]
default_ver = reverse
num_customs = 1

[versions]
reverse = C:\WACCA\Reverse
lily_r = C:\WACCA\Lily R
lily = C:\WACCA\Lily
wacca_s = C:\WACCA\WACCA S
wacca = C:\WACCA\WACCA
offline = C:\WACCA\Offline

[custom_1]
path = C:\WACCA\CustomChartTesting
name = Reverse + Customs
type = reverse
```

You can confirm that the launcher works by starting `WACCALauncher.exe`. You should see some text that 
says `LOADING...`. From here, it will load whatever you set as the default version in your config.

You can interrupt the startup if you press the `TEST` button inside the cab. This should bring up the WACCA Launcher
menu, where you can change your default version, as well as launch a version just once. You can navigate this menu just like you would navigate the test menu in-game.

Now you have to configure the cab to start the launcher when it boots. If you followed the folder structure described above, you should
just be able to run `SetShell.reg` and it will perform the below for you.

Press <kbd>Win</kbd>+<kbd>R</kbd>, type `regedit` and press Enter. Once it has opened, navigate to the
`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\IniFileMapping\system.ini\boot\`
key. Double click the `Shell` value and change the `SYS:` to `USR:Software\`. Navigate to
`HKEY_CURRENT_USER\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\`. Right click in the empty area on the right,
select `New > String Value`, and name it `Shell`. Set the value to the full path of the `WACCALauncher.exe` file.

**Ensure that you put the correct path for your configuration, because if you don't, the system will not boot correctly.**
