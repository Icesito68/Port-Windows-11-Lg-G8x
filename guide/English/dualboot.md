<img align="right" src="https://github.com/Icesito68/Port-Windows-11-Lg-G8x/blob/Lg-G8x/mh2lm.png" width="350" alt="Windows 11 Running On A Lg G8x">

# Running Windows on the LG G8x

## Dualbooting Android and Windows seamlessly

### Prerequisites
- [UEFI image](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/tag/UEFI)
  
- [WOA Helper app](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/download/Dualboot/woahelper.apk)
  
- [StA Installer](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/download/Dualboot/StA_Installer_mh2lm.exe) 

## Setting up the dualboot app
> This guide assumes you are rooted, if you aren't, please do that first

### Setup - Android
> [!NOTE]
> If you are unable to move files to the Windows folder, it means you shut down Windows instead of restarting it. To fix this issue, boot back to Windows and use restart, then as it restarts boot to fastboot and use it to return to Android

- Download and install the WOA Helper app, then open it and grant it root access.
- Download the UEFI image and place it inside the folder named `UEFI` in your internal storage, if this folder does not exist, create it.
- Return to the WOA Helper app and press the `Back up Android boot` button. Select both the `Windows` and `Android` options.
- Press the `Mount Windows` button, then download and move StA_Installer_mh2lm.exe to the newly created `Windows` folder in your internal storage.
- Return to the WOA Helper app and press `Quickboot to Windows`.

### Setup - Windows
- Navigate to `C:\StA_Installer_mh2lm.exe` and run it. If it doesn't work, make sure that any antivirus software is off, as it will probably not let the app run

##### Booting to Android
  - Run the new shortcut on your desktop (you can also pin it to your start menu / taskbar for ease of access)

##### Booting to Windows
  - Press `Quickboot to Windows` inside the app, or use the newly created toggle in your quick settings panel
  
## Finished!

