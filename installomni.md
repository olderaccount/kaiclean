## How to install any app on KaiOS / Firefox OS normally

The sideload is the process of transferring files between two local devices, in particular between a computer and a mobile device. On Firefox OS it was a natural property, and it can be done using ADB and DevTools also on more KaiOS devices (source). The installation of OmniSD is a classic example.
Many devices can sideload third-party apps, but other devices require special patches (check the list). Let's start by seeing how to sideload naturally, before moving on to jailbreak.

### Requirements
1. DEBUG MODE, your device must be able to do this. Normally it is sufficient to dial the debug code *#*#33284#*#* (on Qualcomm), or in addition *#*#0574#*#* (Spreadtrum) to enable the USB debugging;
2. ADB, a versatile command-line tool that allows you to communicate with a device;
3. WEBIDE, the most common and complete of development tools. Choose an old version of Firefox (59 or earlier) or Pale Moon (28.6.1 or earlier), or use the official Kaios emulator (KaiOSRT). Alternatively to WebIDE you can use other command line development tools like Gdeploy, that uses NodeJS, or XPCshell, an XPConnect-enabled JavaScript Shell that lets you run JavaScript code.
