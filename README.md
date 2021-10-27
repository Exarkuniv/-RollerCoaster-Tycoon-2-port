# RollerCoaster-Tycoon-2-port
 RollerCoaster Tycoon 2 port for the Raspberry Pi4


To install 

`wget https://raw.githubusercontent.com/Exarkuniv/-RollerCoaster-Tycoon-2-port/Master/openrct.sh -P $HOME/RetroPie-Setup/scriptmodules/ports/`


Pulled from OpenRCT2 wiki here https://github.com/OpenRCT2/OpenRCT2
_This page is a work in progress by [Gymnasiast](https://github.com/Gymnasiast)._

As of 10 January 2016, OpenRCT2 needs some files from RCT2 in order to run. This page describes which files you need and where to retrieve them.

## Two approaches
You can either do a full install of RCT2 and point OpenRCT2 to its files, or only extract the files you want in order to conserve disk space. If you belong to the first group, you can now skip to _How to retrieve_.

## Required and optional files
_Note: this represents the needed files as of 10 January 2016._
* Data:
  * Required: g1.dat
  * Optional: CSS1.DAT and CSS2.DAT (sound effects)
  * Optional: CSS3.DAT - CSS9.DAT, CSS11.DAT - CSS15.DAT and CSS18.DAT - CSS46.DAT (music styles)
  * Optional: CSS17.DAT (title screen music)
  * Optional: CSS17.DAT from RCT1, renamed to CSS50.DAT, which enables you to have the RCT1 title screen music.
* ObjData:
  * Required: The 772 default RCT2 objects. Easy to identify by sorting on date, since all 772 have a similar timestamp (usually from 2002 or 2003).
  * Optional: The ObjData from Wacky Worlds, Time Twister and any custom content you like.
* Scenarios:
  * Required: If you use the OpenRCT2 title sequence, no scenarios are needed. Six Flags Magic Mountain.SC6 is needed for the RCT2 title sequence.
  * Optional: The standard scenarios from RCT2, and any custom scenarios you like. If you want the RCT1 scenarios, you can use the excellent conversions found here: https://www.mediafire.com/download/3cw47sd2wt3hues/ExactRCT1Recreations.zip
Or the original scenarios from RCT1.
* Tracks:
  * Required: None.
  * Optional: The entire Tracks folder (with the *.TD6 files), which will enable you to select prebuilt rides if you don't want to create them all manually.

If you place those files in the OpenRCT2 folder, it should automatically detect them.

## How to retrieve
The method to retrieve the files varies, as it depends on your operating system (Windows, OS X and various Linux distributions are supported) and your RCT2 media.
  * Disk version
  * [GOG version](https://www.gog.com/game/rollercoaster_tycoon_2)
  * [Steam version](https://store.steampowered.com/app/285330/)
  * Existing install
  * Mini game (follow these instructions if you don't own RCT2)

### Disc version
On Windows, the easiest way is to install RollerCoaster Tycoon 2 and simply point OpenRCT2 to the install directory. On Linux (and possibly macOS?), copy the file `data2.cab` from the CD to a place where you want to extract the files. Then you can use a tool called `unshield` like this:
```
unshield -d extracted/ x data2.cab
```
If unshield throws a `Failed to open data2.cab as an InstallShield Cabinet File`, try
```
unshield -d extracted/ x data1.hdr
```
instead.

This will create a directory "extracted", in which you'll find another directory called "Default_File_Group". That directory contains all the required files.

### Existing install
### RCT Classic + RCT2: Mini Game
RCT Classic contains all the ObjData from RCT2, as well as its other graphics and its tracks. The scenarios are encrypted, but OpenRCT2 is able to decode them. However, the sound effects and music, while present, are in OGG format, which OpenRCT2 cannot yet read. (Adding support for this is tracked in issues [#12237](https://github.com/OpenRCT2/OpenRCT2/issues/12237) and [#10860](https://github.com/OpenRCT2/OpenRCT2/issues/10860).)

Luckily, you can use a demo version of RCT2 for these sound effects. RollerCoaster Tycoon 2: Mini Game (RCT2:MG) is a demo released by Infogrames in 2002. It is very limited in what it can do:
* It does not contain all ObjData. This will prevent many scenarios and saved games from opening.
* It only has three of the scenarios.
* Its scenarios use a different checksum algorithm, which means they will be detected as corrupt. (To use them anyway, you must enable the "Allow loading files with incorrect checksums" option.)

But since the Mini Game does contain all of the music, you can neatly complement your OpenRCT2 install with it if you have RCT Classic. If you have RCT2, it is not needed, and if you have neither, it is useless. In that case, we recommend you obtain RCT2 TTP from GOG or Steam.

#### Obtaining the Mini Game
It can be obtained at no cost from some game sites or one of the following links:
  * [Archive.org mirror](https://archive.org/download/RollerCoasterTycoon2Demos/RCT2_Demo.exe)
  * [Download Free Games mirror](https://www.download-free-games.com/dl/rollercoaster_tycoon2)

#### Using the assets
1. Install RCT Classic and the RCT2 Mini Game.
2. Create a folder somewhere on your hard drive. E.g.: `C:\Users\Owner\RCT2Assets`.
3. From the Mini game, copy the `Data` folder.
4. Create subfolders called `Scenarios`, `ObjData` and `Tracks`.
5. From RCT Classic, copy the following files to their appropriate subfolders:
    * All of the *.pob files to ObjData
    * All of the *.td6 files to Tracks
    * All of the *.sea files to Scenarios
6. Uninstall the Mini Game and RCT Classic, if desired.
7. Start OpenRCT2. When asked to provide the asset path, specify the folder you created in step 2 (e.g. `C:\Users\Owner\RCT2Assets`).
