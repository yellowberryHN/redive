---
title: WACCALauncher
---
# WACCALauncher

WACCALauncher is a tool that automatically launches the game for you
at startup, and also allows you to run multiple versions of WACCA on your cab and switch between them easily.

## Prerequisites

- Game files, set up with [TeamTofuShop's ST](https://gitea.tendokyu.moe/TeamTofuShop/segatools)
- [The latest version of WACCALauncher](https://github.com/YellowberryHN/WACCALauncher/releases/latest)
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
   ├─ WACCALauncher.exe
   ├─ _profiles\
   │  └─ ...
   └─ <other launcher files>
```

For each version you have set up, you will want to create a .json file in the `_profiles` folder, to create a profile in WACCALauncher for it.
Here's an example of what mine looks like for Reverse:

```json
{
	"Name": "Reverse",
	"Type": "WACCA",
	"BasePath": "C:\\WACCA\\Reverse",
	"GamePath": "WindowsNoEditor\\Mercury\\Binaries\\Win64\\Mercury-Win64-Shipping.exe",
	"Configs": [
		"config.json",
		"config_lan_install_server.json",
		"config_region_jpn.json"
	]
}
```

> NOTE: For WACCA and WACCA S, the `config_region_jpn.json` file should be omitted from the config list, and the exe's name is `Mercury.exe`

You can confirm that the launcher works by starting `WACCALauncher.exe`. You should see some text that says `LOADING...`. From here, it will load the default profile, which will be the first file alphabetically if not set.

You can interrupt the startup if you press the `TEST` button inside the cab. This should bring up the WACCALauncher menu, where you can change your default profile, as well as launch a profile manually. You can navigate this menu just like you would navigate the test menu in-game.

Now you have to configure the cab to start the launcher when it boots. ***If you installed WACCALauncher directly into `C:/WACCA`***, you should just be able to run `SetShell.reg`. If not, follow the instructions below.

For more information about configuring WACCALauncher, please check out the [GitHub page](https://github.com/yellowberryHN/WACCALauncher).

>? WARNING: **Manual Auto-Start Instructions**
> Press <kbd>Win</kbd>+<kbd>R</kbd>, type `regedit` and press Enter.
> 
> Once it has opened, navigate to the `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\IniFileMapping\system.ini\boot\` key.
> Double click the `Shell` value and change the part at the beginning that says `SYS:` to say `USR:Software\`.
> 
> Navigate to `HKEY_CURRENT_USER\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\`.
> Right click in the empty area on the right, select `New > String Value`, and name it `Shell`.
> Set the value to the full path of the `WACCALauncher.exe` file.
> 
> **Ensure that you put the correct path for your configuration, because if you don't, the system will not boot correctly.**
