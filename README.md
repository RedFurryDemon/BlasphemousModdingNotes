# BlasphemousModdingNotes

###Introduction
These notes are subjective, they quite possibly *don't* cover all possible tools and options, and I take no responsibility for you accidentally fucking up your install and/or saves. I started writing them first and foremost for my own reference, given that the modding documentation for Blasphemous was practically nonexistent.

Notably, no prior coding experience is necessary to follow these notes (although it's certainly useful).

###Folder structure
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
  
##Graphic replacers  
--graphic replacer (recolor: use GIMP palette)  
--graphic replacer (sprite edits - example: removing pointy part of the helmet)  
--graphic replacer (sprite change - example: flying head -> skull)  
  
##Code editing  
--console enabling and edits (backups, dnSpy, open Assembly, find line, edit method (remove devbuild condition), save)  
https://www.jetbrains.com/decompiler/  
https://github.com/0xd4d/dnSpy/releases  
https://docs.unity3d.com/ScriptReference/Input.GetKeyDown.html  
--https://keycode.info/  
--https://docs.unity3d.com/ScriptReference/KeyCode.html  
--cont. (remapping, check keycode syntax, find backtick key name, replace, save)  
  
--other stuff  
-where is level data? in the .bank files?? I haven't found anything in .xml files so far  
--editing things in Unity editor??  
  
--using dotpeek??  
--as a side note: https://stackoverflow.com/questions/590863/tool-to-compare-dlls-and-disassemble-the-differences  

##Blasphemous Modding API



###Building a mod
Open Visual Studio, go to `File->Open->Folder` and open your `Modding_Code` folder.
