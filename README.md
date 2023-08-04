# Datafrog_SF2000_Vanilla
This repository contains a stripped-down, "vanilla" version of the Datafrog SF2000 Operating System. It provides a clean slate for users to customize and add their own ROMs.

## Disclaimer
All SF2000 OS files are property of Datafrog CN and I do not claim ownership of anything hosted in this repository. This is simply an optimized version of their official OS and has no affiliation with the company.

Please make sure to back up your existing SF2000 microSD card before using this image.

## Tools Needed
- Image writing software to write the .IMG to microSD
  - [usbimager](https://gitlab.com/bztsrc/usbimager) 
OR
  - [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/)

## Instructions
1. Download the [latest version](https://github.com/Dteyn/Datafrog_SF2000_Vanilla/releases/download/v1.5/SF2000_TF_V1.5_20230521-VANILLA.zip) from the [Releases](https://github.com/Dteyn/Datafrog_SF2000_Vanilla/releases) page
2. Open the .ZIP file and extract `SF2000_TF_V1.5_20230521-VANILLA.img`
3. Write the .IMG to your microSD using [usbimager](https://gitlab.com/bztsrc/usbimager) or [Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/).
4. Add your own ROM files to the ROMS folder, then access from the User ROMS / Settings menu, OR
5. Add your own ROMS to the per-console folders using [FROGTOOL](https://github.com/tzlion/frogtool) or [tadpole](https://github.com/EricGoldsteinNz/tadpole)

## Process Used to Clean .IMG file
For reference, here is the process used to clean the .IMG file:

1. Create an image of the original Datafrog SF2000 microSD card using usbimager. Save a copy as backup.
2. Mount the image using [ImDisk Toolkit](https://sourceforge.net/projects/imdisk-toolkit/)
3. Repair the FAT32 filesystem using `CHKDSK /F [Drive Letter]` (see details below)
4. Delete all the ROM files, leaving folder structure intact
5. Run [FROGTOOL](https://github.com/tzlion/frogtool) or [tadpole](https://github.com/EricGoldsteinNz/tadpole) to rebuild the game lists as empty lists
6. Clean the free space on the filesystem using [SDelete](https://learn.microsoft.com/en-us/sysinternals/downloads/sdelete). Command: `SDelete -z [drive letter]`
7. Defragment the filesystem using [UltraDefrag](https://sourceforge.net/projects/ultradefrag/)

Step 5 and 6 are only required for making the .IMG file compress easier, for sharing online. In step 3, deleting the files does not actually remove them from the filesystem which results in a large compressed file. Using SDelete will overwrite the leftover data with zeroes, and defragmenting will move all the data to the beginning of the image.


## Filesystem Errors
Below are the filesystem errors fixed by `CHKDSK /F`:
```
Volume Serial Number is C2A6-503B
Windows is verifying files and folders...
\Resources\Archive.sys  Invalid time stamp.
\Resources\Archive.sys  Invalid time stamp.
\Resources\TSMFK.TAX  Invalid time stamp.
\Resources\TSMFK.TAX  Invalid time stamp.
\Resources\KeyMapInfo.kmp  Invalid time stamp.
\Resources\KeyMapInfo.kmp  Invalid time stamp.
\Resources\KeyMapInfo.kmp  Invalid time stamp.
Removing nonvalid long folder entry from \Resources...
File and folder verification is complete.

Windows has made corrections to the file system.
No further action is required.
   15,258,624 KB total disk space.
           32 KB in 1 hidden files.
        1,120 KB in 20 folders.
       88,384 KB in 196 files.
   15,169,056 KB are available.

       32,768 bytes in each allocation unit.
      476,832 total allocation units on disk.
      474,033 allocation units available on disk.
```

## OS Files Only
Check out Luke7352's repository for the OS files only (not .IMG version):
https://github.com/Luke7352/DatafrogSF2000OS

## More Information about SF2000
Thank you to Von Millhausen for an excellent repository for SF2000 information: https://github.com/vonmillhausen/sf2000

Thank you to tzlion for FROGTOOL, the premier utility for rebuilding game lists: https://github.com/tzlion/frogtool

Thank you to EricGoldsteinNz for tadpole, the best GUI app to manager your SF2000: https://github.com/EricGoldsteinNz/tadpole

Thank you to Zerter for the SF2000 Theme Collection, a great place to customize your Froggy: https://zerter555.github.io/sf2000-collection/

Thank you to the Retro Handhelds Discord: https://discord.gg/retrohandhelds
