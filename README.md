# Datafrog_SF2000_Vanilla

## **Latest version: v1.71 - dated 2023-10-13**

This repository contains a stripped-down, "vanilla" version of the Datafrog SF2000 Operating System. It provides a clean slate for users to customize and add their own ROMs.

## Downloads Available

There are three downloads available: 
1. [Full Image File](#full-image-file) - An IMG file which can be written to microSD using a disk imager (for restoring to factory, minus the ROMs)
2. [Complete OS Files](#complete-os-files) - Only the OS files, which you can copy to a formatted microSD (for starting a fresh build)
3. [Firmware Only](#firmware-only) - Only the `bisrv.asd` file, which you can use to upgrade your firmware

## Full Image File
[**Y_SF2000_TF_V1.71_20231013-VANILLA.zip**](https://github.com/Dteyn/Datafrog_SF2000_Vanilla/releases/download/v1.71/Y_SF2000_TF_V1.71_20231013-VANILLA.zip)

This is the original .IMG file as supplied by Data Frog, but with the ROMs removed, making it a much smaller download. This can be used to re-image your microSD and your system will be able to boot with this image even if the Bootloader Bugfix is not applied. Once booted, be sure to fix the [Bootloader Bug](https://github.com/vonmillhausen/sf2000#bootloader-bug).

To write the .IMG to microSD, see the instructions below 

#### Changes to .IMG from stock:
- All ROMs removed
- Ran frogtool to rebuild empty game lists
- FAT32 filesystem repaired using chkdsk
- Defragmented and optimized

### Tools Needed
- Image writing software to write the .IMG to microSD
  - [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/)

### Instructions (.IMG file for writing to microSD)
1. Download [**Y_SF2000_TF_V1.71_20231013-VANILLA.zip**](https://github.com/Dteyn/Datafrog_SF2000_Vanilla/releases/download/v1.71/Y_SF2000_TF_V1.71_20231013-VANILLA.zip)
2. Open the .ZIP file and extract `Y_SF2000_TF_V1.71_20231013-VANILLA.img`
3. Write the .IMG to your microSD using [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/).
4. Add your own ROM files to the ROMS folder, then access from the User ROMS / Settings menu, OR
5. Alternatively, add your own ROMS to the per-console folders using [FROGTOOL](https://github.com/tzlion/frogtool) or [tadpole](https://github.com/EricGoldsteinNz/tadpole)

### Process Used to Clean .IMG file
For reference, here is the process I use to clean the .IMG file:

1. Obtain an image of the original Datafrog SF2000 firmware.
2. Mount the image using [ImDisk Toolkit](https://sourceforge.net/projects/imdisk-toolkit/)
3. Delete all files except contents of `/bios` and `/Resources`, leaving folder structure intact
4. Fix the [filesystem errors](#filesystem-errors) using `CHKDSK /F [Drive Letter]` (see details below)
5. Run [FROGTOOL](https://github.com/tzlion/frogtool) or [tadpole](https://github.com/EricGoldsteinNz/tadpole) to rebuild the game lists as empty lists
6. Zero the free space on the filesystem using [SDelete](https://learn.microsoft.com/en-us/sysinternals/downloads/sdelete). Command: `SDelete -z [drive letter]`
7. Defragment the filesystem using [UltraDefrag](https://sourceforge.net/projects/ultradefrag/)

Step 6 and 7 are only required for making the .IMG file compress easier, for sharing online. In step 3, deleting the files does not actually remove the data from the filesystem which results in a large compressed file. Using SDelete will overwrite the leftover data with zeroes, and defragmenting will move all the data to the beginning of the image.


### Filesystem Errors
The original .IMG from Datafrog has filesystem errors, which results in Windows prompting 'This drive has a problem' and recommending it be fixed. This image has had those filesystem errors repaired already using CHKDSK.

Below are the filesystem errors fixed by `CHKDSK /F`:
```
The type of the file system is FAT32.
Volume Serial Number is C2A6-503B
Windows is verifying files and folders...
\Resources\Archive.sys  Invalid time stamp.
\Resources\History.bin  Invalid time stamp.
\Resources\TSMFK.TAX  Invalid time stamp.
Removing nonvalid long folder entry from \FC\save...
Removing nonvalid long folder entry from \SFC\save...
File and folder verification is complete.

Windows has made corrections to the file system.
No further action is required.
```

## Complete OS Files
[**DATAFROG-SF2000-1.71-OS-Files.zip**](https://github.com/Dteyn/Datafrog_SF2000_Vanilla/releases/download/v1.71/DATAFROG-SF2000-1.71-OS-Files.zip)

Instead of a .IMG file, this archive contains all files from the `/bios` and `/Resources` folders. You can use this if you already have the Bootloader Bug fixed, and are building a new microSD. Simply format the microSD, copy these files over, then add your own ROMS and use [tadpole](https://github.com/EricGoldsteinNz/tadpole) to customize further.

## Firmware Only
[**bisrv-v1.71-10_13.zip**](https://github.com/Dteyn/Datafrog_SF2000_Vanilla/releases/download/v1.71/bisrv-v1.71-10_13.zip)

This archive contains only the `bisrv.asd` file from the `/bios` folder. If all you want to do is upgrade the firmware on your existing microSD, this is all you need. The only file that changed between v1.5, v1.6 or v1.71 is `bisrv.asd` file, which means you only need to replace this file to upgrade. Just copy the file into the `/bios` folder and replace the existing `bisrv.asd`.

  - File size: 12,624,628 bytes
  - Date: October 13, 2023, 5:56:56 AM
  - CRC32: 33B9FB14

## Disclaimer
All SF2000 OS files are property of Datafrog CN and their resepctive partners. I do not claim ownership of anything hosted in this repository.

## More Information about SF2000
See my other SF2000 projects here: https://dteyn.github.io/sf2000_projects.htm

Thank you to Von Millhausen for an excellent repository for SF2000 information: https://github.com/vonmillhausen/sf2000

Thank you to tzlion for FROGTOOL, the premier utility for rebuilding game lists: https://github.com/tzlion/frogtool

Thank you to EricGoldsteinNz for tadpole, the best GUI app to manage your SF2000: https://github.com/EricGoldsteinNz/tadpole

Thank you to Zerter and Kev for the SF2000 Collection, a great place to customize your Froggy: https://zerter555.github.io/sf2000-collection/

Thank you to the Retro Handhelds Discord: https://discord.gg/retrohandhelds
