# Blasphemous Modding Notes
  
### Introduction
These notes are subjective, they quite possibly *don't* cover all possible tools and options, and I take no responsibility for you accidentally fucking up your install and/or saves. I started writing them first and foremost for my own reference, given that the modding documentation for Blasphemous was practically nonexistent. Needless to say, they're still extremely incomplete.  
  
Notably, no prior image editing/coding experience is necessary to follow these notes (although it's certainly useful).  
  
### Folder structure
For the purposes of these notes, I will be using the following folder structure and names:
```
Steam\steamapps\common\Blasphemous (= ROOT folder)
--Blasphemous_Data (= DATA folder; vanilla folder which holds game data, obviously)
----Managed (vanilla .dll files)
------Mods (added when copying edited .dll files from Output)
--Blasphemous_Data_BACKUP (unedited copy of vanilla game data, in case of a fuckup)
--Goodies (vanilla folder with additional stuff like the official artbook or comic)
--Modding_Code (modding API, and any mod source code)
--Modding_Graphics_Export (unpacked data.unity3d, and unedited .png images exported from it)
--Modding_Graphics_Import (edited .png images, and .psd or .xcf source files)
--Modding_Tools (includes Save Editor and various other things)
```
The two `Modding_Graphics_` folders are irrelevant unless you want to mod the sprites (that is, graphic assets).  
  
To save hard drive space, I did not back up all of the game data; for any sort of modding I describe in these notes, it is actually enough to back up up to two files:  
- `data.unity3d` (in the ROOT folder) - back it up if you plan to do graphic modding  
- `Assembly-CSharp.dll` (in DATA, in the `Managed` folder) - back it up if you plan to do code editing  
  
---
  
## Graphic replacers  
**Requirements:** Gimp, UABE  
  
### Preparations  
--write how to extract stuff with UABE!!!  
### Example: Removing shadow from text screens
Perhaps the header itself is a bit misleading: I mean the screens that say `REQUIEM AETERNAM`, `DETESTATIO SACRORUM`, or `SUMMA BLASPHEMIA`.  
1. Find the .png files you want to edit in `Modding_Graphics_Export`. Note that depending on the sprite you're modding, it might not be easy to find the correct file. When in doubt, use a quick and simple test: open the .png you suspect might be the one you're looking for. Fill the whole background with some color (or make another big, noticeable change), and import the result into your game data. If you can notice the change in-game in the place you expect it, it means it's the correct asset.  
  
Example:  
![checking which assets are needed](images/Modding_graphic_test_01.png)  
  
Anyway, the assets needed here are:  
```
boss_defeated_screen_title-sharedassets1.assets-66.png
confessor_area_screen_title-sharedassets1.assets-38.png
pontiff_defeated_screen_title-sharedassets1.assets-54.png
```
2. Open them all in GIMP.  
3. Select the black parts (best tool for that is `Select by color`); note that there are a few different shades used, so if the selection treshold is 0, you'll need to click each of them (in `Mode`, you can use the second option, `Add`, which adds the newly selected area to existing selection instead of replacing it). Remember to **uncheck** `Antialiasing` and `Feather edges`. Delete using `del` or `Ctrl + X`.  
4. While editing `REQUIEM AETERNAM`, I also noticed that the different shades of orange look bad without the background, so I decided to use only one shade. However, it turns out only the `AE` is problematic (I checked by selecting by color the main part of the text, and the alpha background - 2 clicks with treshold 0, and then inverted the selection to see which parts had anything other than these two colors). I ended up simply editing that letter by hand, using 1-pixel brush.  
  
Before and after (selection to show edited parts):  
![image editing](images/Modding_graphic_shades_01.png)  
5. Then I decided to slightly alter the color of `SUMMA BLASPHEMIA` text to add some more blue. This can be done for example by editing the color palette. Go to `Windows -> Dockable dialogs -> Colormap`. Double-click the color you want to edit. I changed it from `#ca439f` to `#8943ca`.  
  
Palette editing in GIMP:
![palette editing in GIMP](images/Modding_graphic_colormap_01.png)  
6. Save the .png files in `Modding_Graphics_Import` and put them in the game assets using UABE.  
  
--graphic replacer (sprite change - example: flying head -> skull)  
  
---
  
## Code editing  
### In-game console  
The debug console is included in the vanilla game, but it is normally not accessible to the users. There is a mod that *should* enable the console: [Blasphemous Debug Console](https://www.nexusmods.com/blasphemous/mods/2) - however, it does not work for some users (including myself), and seems to be based on an earlier version of the game than the one currently available on Steam. Enabling the console on your own takes around a minute, probably much less than it would take to get the mod to work with the updated game version.  
  
I used [dnSpy](https://github.com/0xd4d/dnSpy/releases) to enable the console.  
1. Open dnSpy.  
2. Open `Assembly-CSharp.dll` with it (use the version from your `Managed` folder, not the backup version!)  
3. Find the window `Assembly Explorer` and go to `Assembly-CSharp (0.0.0.0) -> Assembly-CSharp.dll -> Gameplay.UI.Widgets`  
4. Double-click on `ConsoleWidget`.  
5. Hit `Ctrl + F` and enter `isDebugBuild` in the search bar to find the line that you want to edit.  
The full line should look like this:  
```
			if (Input.GetKeyDown(KeyCode.F1) && Debug.isDebugBuild)
```
6. Right-click on *the empty space* next to that line. Go to `Edit Method (C#)...`.  
Modify it to look like this:
```
			// if (Input.GetKeyDown(KeyCode.F1) && Debug.isDebugBuild)
			if (Input.GetKeyDown(KeyCode.F1))
```
The first line is the original one, but commented out with `//` - that is, it's inactive. With small tweaks like this, I prefer to leave the original line commented out, in case I wanted to use it later. However, it could also simply be deleted with no effect upon the game itself.
The second line had a part of its condition removed - so that, in simple words, the console would work on regular (non-testing) versions of the game.
In the same line, the console hotkey can be changed. For example, being an MW modder used to bringing up the console with a backtick ( \` ), I found it much more convenient to open Blasphemous console in the same way. Thus, my edit looks like this:
```
			// if (Input.GetKeyDown(KeyCode.F1) && Debug.isDebugBuild)
			if (Input.GetKeyDown(KeyCode.BackQuote))
```
Unity key code reference is available [here](https://docs.unity3d.com/ScriptReference/KeyCode.html).  
7. Click `Compile`, go to `File -> Save Module`, and click `OK` in the saving options.  
8. Open the game. If you've done everything correctly, you should be able to access the console with the hotkey of your choice.  
  


other stuff: 
https://www.jetbrains.com/decompiler/  
 
https://docs.unity3d.com/ScriptReference/Input.GetKeyDown.html  
--https://keycode.info/  
--https://docs.unity3d.com/ScriptReference/KeyCode.html  
--cont. (remapping, check keycode syntax, find backtick key name, replace, save)  
  
--more other stuff  
-where is level data? in the .bank files?? I haven't found anything in .xml files so far  
--editing things in Unity editor??  
  
--using dotpeek??  
--as a side note: https://stackoverflow.com/questions/590863/tool-to-compare-dlls-and-disassemble-the-differences  

## Blasphemous Modding API

describe how to use it to begin with
and first use the testing mod

### Building a mod
Open Visual Studio, go to `File->Open->Folder` and open your `Modding_Code` folder.
