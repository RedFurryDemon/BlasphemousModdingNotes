## Basics
  
### Terms  
Modding and code/asset editing use specific terminology; here I provide a short overview of some basic terms I'll be using in these notes.  
  
**Alpha** - image transparency  
**Asset** - image, video, sound, or other file used for something in the game (for example, an NPC, level design, etc.); in broader sense, any file used by the game  
**Level** - in Blasphemous, a level is one "room"; so every area consist of at least one level (usually more)
**Palette** - skin for the Penitent One
**Vanilla** - unmodded, original game or assets  
  
---
  
### File and folder structure
Here are some of the files and folders relevant to modding the game:
  
```
\Blasphemous (= ROOT folder; base folder of the game)
--\Blasphemous_Data (= DATA folder; folder which holds game data, obviously)
--\--\data.unity3d (contains assets for palettes, sprites of the Penitent One, enemy sprites, and UI images)
--\--\Managed (folder with .dll files containing code used in the game)
--\--\--\Assembly-CSharp.dll (file containing game logic and generally important stuff)
```

The two `Modding_Graphics_` folders are irrelevant unless you want to mod the sprites (that is, graphic assets).  
  
To save hard drive space, I did not back up all of the game data; for any sort of modding I describe in these notes, it is actually enough to back up up to two files:  
- `data.unity3d` (in the ROOT folder) - back it up if you plan to do graphic modding  
- `Assembly-CSharp.dll` (in `Blasphemous_Data\Managed`) - back it up if you plan to do code editing  
  
---
  
### Software
**[dnSpy](https://github.com/0xd4d/dnSpy/releases)** is a free C# decompiler. It allows editing the game code.  
**[GIMP](www.gimp.org)** (GNU Image Manipulation Program) is a free and open-source image editing software with many functions and plugins available. Photoshop may be used instead.  
**[UABE](https://github.com/DerPopo/UABE/releases/)** (Unity Asset Bundle Extractor) is a free tool to browse some of Unity files. It can also be used to create automatic installers for graphic replacers.  
  
---
  
### Useful things
--1. The console!!!  
--2. Save editor and basic knowledge of save editing.  
--3. A save file that can be used for testing without fear of fucking something up (preferably one that is already at 100% and backed up).  
--4. Enabled Prie Dieu teleporting on your test save, regardless of what you think about using teleportation during a playthrough.  