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

![using WebIDE on a device in "normal mode"](https://ivan-hc.github.io/bananahackers/install-omnisd/6481130aafd06e6d5dcf736a5ef6d55e.jpg)

using WebIDE on a device in "Privileged mode"
   
