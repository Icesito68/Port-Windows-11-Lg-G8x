<img align="right" src="https://github.com/Icesito68/Port-Windows-11-Lg-G8x/blob/Lg-G8x/mh2lm.png" width="350" alt="Windows 11 Running On A Lg G8x">

# Running Windows on the LG G8x

## Dualbooting Android and Windows seamlessly

### Prerequisites
- [UEFI image](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/tag/UEFI)
  
- [WOA Helper app](https://github.com/Marius586/WoA-Helper-update/releases/tag/WOA)
  
- [StA Installer](https://github.com/Icesito68/Port-Windows-11-Lge-devices/releases/download/Dualboot/StA_Installer_mh2lm.exe) 

## Setting up the dualboot app
> This guide assumes you are rooted, if you aren't, please do that first

### Setup - Android
- Download and install the WOA Helper app, then open it and grant it root access.
- Download the UEFI image and place it inside the folder named `UEFI` in your internal storage.
- Press the `Mount Windows` button, then download and move **StA_Installer_mh2lm.exe** to the newly created `Windows` folder in your internal storage.
> [!Important]
> If `/sdcard/Windows` is empty, your rom does not support mounting and you will have to make a boot.img backup inside the app, then copy it manually to Windows once you boot to it (for example by uploading it somewhere and then downloading it while booted into Windows). The same applies to the STA files.
>
> Do the same thing if the folder is read-only.
- Return to the WOA Helper app and press `Quickboot to Windows`.

### Setup - Windows
- Navigate to `C:\StA_Installer_mh2lm.exe` and run it. If it doesn't work, make sure that any antivirus software is off, as it will probably not let the app run

#### Booting to Android
- Run the new shortcut on your desktop (you can also pin it to your start menu / taskbar for ease of access)

#### Booting to Windows
- Press `Quickboot to Windows` inside the app, or use the newly created toggle in your quick settings panel
  
## Finished!









