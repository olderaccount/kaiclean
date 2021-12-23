## How to install any app on KaiOS / Firefox OS normally

The sideload is the process of transferring files between two local devices, in particular between a computer and a mobile device. On Firefox OS it was a natural property, and it can be done using ADB and DevTools also on more KaiOS devices (source). The installation of OmniSD is a classic example.
Many devices can sideload third-party apps, but other devices require special patches (check the list). Let's start by seeing how to sideload naturally, before moving on to jailbreak.

### Requirements
1. DEBUG MODE, your device must be able to do this. Normally it is sufficient to dial the debug code *#*#33284#*#* (on Qualcomm), or in addition *#*#0574#*#* (Spreadtrum) to enable the USB debugging;
2. ADB, a versatile command-line tool that allows you to communicate with a device;
3. WEBIDE, the most common and complete of development tools. Choose an old version of Firefox (59 or earlier) or Pale Moon (28.6.1 or earlier), or use the official Kaios emulator (KaiOSRT). Alternatively to WebIDE you can use other command line development tools like Gdeploy, that uses NodeJS, or XPCshell, an XPConnect-enabled JavaScript Shell that lets you run JavaScript code.
4. 
### Proceedings

1.    Enable the debug mode on your device;

2.    Connect the device to the PC using a USB cable;

3.    Open WebIDE and connect to the "Remote runtime" (this should work on the official Kaiostr emulator), if not seen, start the "adb forward tcp:6000 localfilesystem:/data/local/debugger-socket" command and click again on "Remote runtime". If an error message about build date mismatch appears, you can safely ignore it. If the connection doesn't work, try rebooting the phone, running the "adb forward" command and connecting again.

4.    Select the application's folder in the "Open packaged app" button of WebIDE.

5.    With the triangular "Play button" at the top center of WebIDE, the app will be installed on your phone.

## Jailbreak on KaiOS: all you need to know
   ### Difference between "normal sideload" and "Jailbreak"
The official jailbreak method differs from the normal sideload only in the fact that, after point 5, a "privileged factory reset" is required directly from the jailbreak application that we will install (OmniSD, Wallace or Wallace-Toolbox) by pressing the # key from it, in order to automatically activate all the "Developer" options. After the reset, you will need to repeat the whole procedure if you want to use these applications for a different use (sideload without PC or root permissions).
   ### Difference between "Jailbreak" and "Root"
    Jailbreak is a process that enables the development menu and allows installing third-party apps.

    Rooting is a process that allows root-level of ADB console access (for more info visit the "ROOT" section).

## Privileged mode
The privileged mode, as the word itself says, is a boot mode in which the user has full control over the development tools and hidden components of the device, such as the "Developer" menu in the "Settings" app, you can also debug on the pre-installed applications and access the "Device Preferences" from WebIDE.
This mode still allows you to obtain updates, and can be removed simply by performing a normal factory reset from the Settings app or from Recovery mode.

using WebIDE on a device in "normal mode
![using WebIDE on a device in "normal mode"](https://ivan-hc.github.io/bananahackers/install-omnisd/6481130aafd06e6d5dcf736a5ef6d55e.jpg)

using WebIDE on a device in "Privileged mode"
![using WebIDE on a device in "Privileged mode"](https://ivan-hc.github.io/bananahackers/install-omnisd/4100ca0f10a4bc275ea1c92b15b49f84.jpg)
   
## Developer menu
The "Developer" menu allows you to debug on a device, in addition to accessing ADB and DevTools, as well as various other utilities that can be consulted here. It is hidden inside the "Settings" app, and is visible only when the device is in "privileged mode".

## How jailbreak works on KaiOS (diagram)
After two years of research, we have finally come to a precise pattern on how jailbreak works on different KaiOS devices. The approach is based on the type of processor used on the device, Qualcomm, Spreadtrum or Mediatek. Thanks to this study, we managed to jailbreak many different KaiOS devices. This diagram is provided by     
         SITUATION 1, typical of Qualcomm-based devices. If the code *#*#33284#*#* needed for debugging works, we must verify if we have access to ADB and WebIDE. If all goes well we can use OmniSD or Wallace Toolbox to get the jailbreak;

    SITUATION 2, typical of Spreadtrum-based devices. If the code *#*#33284#*#* needed for debugging works, we must verify if we have access to ADB and WebIDE. If the result is negative, enable debugging using the code *#*#0574#*#* and retry the access to ADB and WebIDE. If all goes well we can use Wallace-toolbox to get the jailbreak;

    SITUATION 3, typical of Mediatek-based devices. The debug code does not work, let's check if Fastboot is available. If we have it, let check if it is possible to flash the "cache" partition. If all goes well, use the so-called "cache injection" method, and we will get the "Developer" menu;

    SITUATION 4, typical for all the locked devices. The debug code does not work and Fastboot is not available even to flash the partitions. Let's check if we have other tools to flash the partitions. If yes, we can use the "cache injection" method, and we will get the "Developer" menu;

    SITUATION 5. The debug code does not work, Fastboot is not available and we don't even have tools to flash the partitions. Jailbreak is not possible yet.
    
diagram
![](https://ivan-hc.github.io/bananahackers/install-omnisd/5d9dac0755d71c8c6e60071c514897f3.jpg)

As you can see, not all KaiOS devices have the same possibilities. To help users better understand which installation method is more suitable, have classified KaiOS devices. Learn more [here](devices.md)

## W2D: enable the Developer menu from the browser
This new method was born on Discord from an idea of ​​Luxferre and Tbrrss on September 22, 2020 and is ideal for temporarily bringing up the Developer menu, so that you can enable easily ADB and DevTools.

This is probably the easiest and most versatile way of jailbreaking most existing KaiOS-based phones. We decided to call it W2D (web-to-dev) because it's based on the hidden but totally official (as confirmed by Fabrice, KaiOS architect) fact that MozActivity class is visible from the browser context.

It just calls a hidden activity in the Settings app that opens the developer menu directly:

new MozActivity({name: "configure", data: {target: "device", section: "developer"}})

As for usage, it's very simple for most KaiOS phones:

1. Go to https://w2d.bananahackers.net from the phone's browser and click "Launch Developer menu". Alternativelly use https://dorime.surge.sh/ and click on the "DORIME 2" button, in both cases this will open the hidden Developer Menu;
2. Enable first ADB, then "ADB & DevTools" in the Debugger menu item. Check that the bug icon appears in the panel;

3. Ensure that ADB and WebIDE connection works, connect via WebIDE or gdeploy and install Wallace Toolbox version 0.0.5 or higher or OmniSD;

4. Using Wallace Toolbox, just select # key ("Enable developer menu") and reboot the phone when prompted, or perform a privileged factory reset using OmniSD;

5. After reboot, ensure that the Developer menu is still present in the Settings > Device and you can connect to the phone in privileged mode.

NOTE that for the [Doro-branded KaiOS devices](doro.md), all installation can currently only be done in FFBM mode because of the way ADB server is launched there.


## What is OmniSD and why it is so important
OmniSD is a third-party application for KaiOS, developed by Luxferre in August 2018, and like other applications it is written in HTML, JavaScript and CSS. The weight of the installation is approximately 58 kilobytes. You can download the standalone OmniSD package from here (alternative links here or here).

OmniSD detects packaged applications in zip format present in the "downloads" or the "apps" folder of the sd card or the internal memory to then install them (jailbreak).

Another feature of this application is the ability to get a "Privileged Factory Reset" by pressing the # key while the app is running. This enable the "Developer" menu within the "Settings" application on the system, allowing the user to access ADB and DevTools directly from the menu.

OmniSD accepts app packages in the .zip format. An archive must contain three files:

    application.zip file (with the actual WebIDE-compatible KaiOS/FFOS app);

    update.webapp file (can be empty but must be present);

    metadata.json file in the following format:

{"version": 1, "manifestURL": "app://[your_app_id]/manifest.webapp"},

where [your_app_id] has to be replaced with the actual ID (origin) of your app registered in the manifest, and manifest.webapp has to be renamed if it's called differently in the application.zip archive. Other than that, the application structure in application.zip must match the general KaiOS and Firefox OS app structure. Learn more [here](firstapp.md)

## Other applications similar to OmniSD
Luxferre has created various projects, including a custom privacy-oriented rom (GerdaOS) and a real library of extensions and various tools for KaiOS. Here are some applications developed by him, containing some features in common with OmniSD:

    GerdaOS File Manager, a modified version of the stock File Manager for KaiOS, that installs omnisd packages by not limiting itself to the "download" and "app" folders, unlike OmniSD;

    Wallace (see the "Temporary Root" page) is an application that enables root privileges and can perform "privileged reset". A classic version, a light version (without adbd binary file) and an optimized version for devices with Spreadtrum chipset are available for this app;

    Wallace-Toolbox (see the "Temporary Root" page) is the evolution of Wallace, which includes the same functions and various tools, such as the call recorder (KaiOS 2.5.2) and an IMEI repairer.
    
## Best safe Jailbreak methods
[OFFICIAL JAILBREAK, perform a "privileged factory reset" using OmniSD](officialjb.md)
[Cache injection, the best method (without OmniSD)](cacheinjection)
[MANUAL JAILBREAK, enable ADB & DevTools on the /data partition (without OmniSD)](enableadbdevtools.md)
[MANUAL DATA PATCH, put OmniSD directly on the /data partition](omnisdmanualinstall.md)

## Extreme and unsafe jailbreak method
Also known as Omnijb-final.zip or Smith.zip , the extreme method means stopping updates permanently. This guide is obsolete, not recommended and for educational purposes only! Use at your own risk [here](extremejb.md)


##Gerda File Manager, PKG & GAB
Install omnisd packages from the file manager, learn more [here](gerdafilespkg.md)
