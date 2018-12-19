NEOS
======

This is the operating system for your [EON Gold Dashcam DevKit](https://comma.ai/shop/products/eon-gold-dashcam-devkit)

It's open source; you can find the repo needed to build NEOS [here](https://github.com/commaai/eon-neos-builder)

Automatic Update
------

When the time comes, you won't have to do anything, and this should just automatically update your EON Gold. This is the recommended option for most people.

Manual Update / Restore
------

Requirements: git-lfs, fastboot, tar

Clone this repo. Hold power and volume down to enter fastboot mode on your EON Gold. Then run:

```
./download.sh
./flash.sh
```

<b>NOTE: This will wipe your EON Gold</b>

<b>Unlocking</b>
------

The phone used in the EON Gold is the LeEco Le Pro 3. This phone comes in various models LEX720, LEX725, LEX727 usually referred to as X720, X725 and X727. The phone often comes locked and unlocking via Developer Options (https://lifehacker.com/the-coolest-features-you-can-unlock-in-androids-develop-1789517222) may not be sufficient to grant permission to Unlock and Flash the device.

Careful note should be taken to see what model your phone is as instructions appear to vary online based on model #. The following has been confirmed working on the LEX727 (X727).

Download the file "x727-5.8.019s_bootloader-unlock.zip" from https://www.androidfilehost.com/?fid=313042859668275431 and Extract the file "emmc_appsboot.mbn" and place it in your bootloader/ADB folder.

- Run "fastboot flash aboot emmc_appsboot.mbn" (Yes, "aboot")
- Now Reboot into Bootloader again ("fastboot reboot bootloader")
- You can now unlock the phone ("fastboot oem unlock-go")

<b>Installing from Windows</b>
------

Should Linux not be readily available, here are Step by Step instructions for Windows machines:

1) Clone or Download this Github Repo
2) Download and Install 7-Zip (7-zip.org). Copy all files from Program Files to a new folder "c:\7z" for easier access
3) Extract all .GZ files in the images folder ("c:\7z\7z x *.gz")
4) Extract all .tar files in the images folder ("c:\7z\7z x *.tar")

5) Download and Setup ADB (https://www.xda-developers.com/install-adb-windows-macos-linux/)
6) Put your phone in Fastboot Mode (Hold down Power Button + DOWN arrow, note that Power+UP = Recovery Mode) and ensure is charged as well as connected to your PC
7) In the "platform-tools" folder, ensure that the phone is listed ("adb devices")

Now, attempt to do a Flash. Should this fail, follow the instructions in the "Unlocking" section.

8) Run "fastboot flash boot boot.img"
9) Run "fastboot flash recovery recovery.img"
10) Run "fastboot flash system system.img"

Now to do cleanup.

11) Run "fastboot format:ext4 cache
12) Run "fastboot format:ext4 userdata
13) Run "fastboot reboot" to Reboot the phone

Your phone should now be ready to go and install OpenPilot. Note that Chffr Plus does not appear to be installed, so it does not need to be uninstalled.
