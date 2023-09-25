# Datafrog_SF2000_Vanilla
This repository contains a stripped-down, "vanilla" version of the Datafrog SF2000 Operating System. It provides a clean slate for users to customize and add their own ROMs.

There are two options available: a .IMG file which has been cleaned up and can be written to a microSD, as well as an "OS Only" archive which contains only the OS files.

**Latest version: v1.6 - aka 2023-08-03** (`bisrv.asd` dated 2023-07-10)

## Disclaimer
All SF2000 OS files are property of Datafrog CN and I do not claim ownership of anything hosted in this repository. This is simply an optimized version of their official OS and has no affiliation with the company.

Please make sure to back up your existing SF2000 microSD card before using this image.

## Tools Needed
- Image writing software to write the .IMG to microSD
  - [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/)

## Instructions (.IMG file for writing to microSD)
1. Download the [latest version](https://github.com/Dteyn/Datafrog_SF2000_Vanilla/releases/download/v1.6/SF2000_TF_20230803-VANILLA.zip) from the [Releases](https://github.com/Dteyn/Datafrog_SF2000_Vanilla/releases) page
2. Open the .ZIP file and extract `SF2000_TF_20230803-VANILLA.img`
3. Write the .IMG to your microSD using [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/).
4. Add your own ROM files to the ROMS folder, then access from the User ROMS / Settings menu, OR
5. Alternatively, add your own ROMS to the per-console folders using [FROGTOOL](https://github.com/tzlion/frogtool) or [tadpole](https://github.com/EricGoldsteinNz/tadpole)

## Process Used to Clean .IMG file
For reference, here is the process used to clean the .IMG file:

1. Create an image of the original Datafrog SF2000 microSD card using usbimager. Save a copy as backup.
2. Mount the image using [ImDisk Toolkit](https://sourceforge.net/projects/imdisk-toolkit/)
3. Delete all the ROM files, leaving folder structure intact
4. Repair the FAT32 filesystem using `CHKDSK /F [Drive Letter]` (see details below)
5. Run [FROGTOOL](https://github.com/tzlion/frogtool) or [tadpole](https://github.com/EricGoldsteinNz/tadpole) to rebuild the game lists as empty lists
6. Zero the free space on the filesystem using [SDelete](https://learn.microsoft.com/en-us/sysinternals/downloads/sdelete). Command: `SDelete -z [drive letter]`
7. Defragment the filesystem using [UltraDefrag](https://sourceforge.net/projects/ultradefrag/)

Step 6 and 7 are only required for making the .IMG file compress easier, for sharing online. In step 3, deleting the files does not actually remove them from the filesystem which results in a large compressed file. Using SDelete will overwrite the leftover data with zeroes, and defragmenting will move all the data to the beginning of the image.


## Filesystem Errors
Below are the filesystem errors fixed by `CHKDSK /F`:
```
The type of the file system is FAT32.
Volume Serial Number is C2A6-503B
Windows is verifying files and folders...
\Resources\Archive.sys  Invalid time stamp.
\Resources\History.bin  Invalid time stamp.
\Resources\TSMFK.TAX  Invalid time stamp.
Removing nonvalid long folder entry from \FC\save...
File and folder verification is complete.

Windows has made corrections to the file system.
No further action is required.
```

## OS Files Only
The OS Only archives are also available to download. Instead of writing the entire .IMG file as above, you can also format a microSD and use the OS files (linked below) to create your own custom microSD.

NOTE: With this method, you may run into the [Bootloader Bug](https://github.com/vonmillhausen/sf2000#bootloader-bug). Before creating a custom microSD, it's recommended to apply the bootloader bugfix to avoid running into the issue.

There are two archives available for the OS files:

- [**DATAFROG-SF2000-08.03-OS-Files-Only-VANILLA.zip**](https://github.com/Dteyn/Datafrog_SF2000_Vanilla/releases/download/v1.6/DATAFROG-SF2000-08.03-OS-Files-Only-VANILLA.zip) - This version has had frogtool run to rebuild the game lists with 0 games.

- [**DATAFROG-SF2000-08.03-OS-Files-Only-STOCK-no_roms.zip**](https://github.com/Dteyn/Datafrog_SF2000_Vanilla/releases/download/v1.6/DATAFROG-SF2000-08.03-OS-Files-Only-STOCK-no_roms.zip) - These are the untouched, stock OS files from the 2023-08-03 microSD without any changes (aside from removing ROMs)


## More Information about SF2000
Thank you to Von Millhausen for an excellent repository for SF2000 information: https://github.com/vonmillhausen/sf2000

Thank you to tzlion for FROGTOOL, the premier utility for rebuilding game lists: https://github.com/tzlion/frogtool

Thank you to EricGoldsteinNz for tadpole, the best GUI app to manage your SF2000: https://github.com/EricGoldsteinNz/tadpole

Thank you to Zerter for the SF2000 Collection, a great place to customize your Froggy: https://zerter555.github.io/sf2000-collection/

Thank you to the Retro Handhelds Discord: https://discord.gg/retrohandhelds
