## In-game console  
The debug console is included in the vanilla game, but it is normally not accessible to the users. It is extremely useful for testing mods and previewing how vanilla game behaves without having to play through the whole content normally.  
  
What the console **should not** be used for is speedrunning and getting achievements (unless you're doing it only to stroke your ego, I suppose?).  
  
There is a mod that *might* enable the console: [Blasphemous Debug Console](https://www.nexusmods.com/blasphemous/mods/2) - however, it does not work for some users (including myself), since it seems to be based on an earlier version of the game than the one currently available on Steam. Enabling the console on your own takes around a minute, probably much less than it would take to get the mod to work with the updated game version.  
  
### Enabling the console  
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
--add note that the comments aren't preserved, and best to save the decompiled source file!!!
7. Click `Compile`, go to `File -> Save Module`, and click `OK` in the saving options.  
8. Open the game. If you've done everything correctly, you should be able to access the console with the hotkey of your choice.  
  
### Console commands  
```
execution
execution y
execution n
```
Something to do with executions, needs testing.  
  
```
flag
flag set IDFLAG
flag clear IDFLAG
flag test IDFLAG
```
Possibly related to quest states?  
  
```
graybox
```
???  
  
```
help
```
Displays a list of available commands.  
  
```
invincible
```
Enables/disables invulnerability mode: the Penitent One's health isn't affected by enemy attacks or contact damage, and dying on the spikes respawns him in the last stable spot. Fervour still decreases normally, and flasks aren't refilled automatically. Note that this command might be buggy when the Penitent One falls into the depths (teleporting via the console might help in such a case).  
  
```
invtest
```
Adds all items (rosary beads, prayers, Mea Culpa hearts, etc.) **Don't use this if you haven't gotten the relevant achievements yet, as it's not possible to remove Steam achievements!**  
--todo - check Steam Achievement Manager and other possible solutions?  
  
```
kill all
```
Kills all entities in the current level. This includes the enemies **and** the player; also frees caged cherubs. NPCs - not tested yet.  
  
```
kill player
```
```
kill player prieudieu
```
```
kill NAME
```
```
language
language list
language current
language set LANGUAGE_CODE
```
These commands are related to language of the UI.  
  
```
load
```
This command is helpful in quickly traversing a level. It seems to work if you use it in one level and then use the door to go to another one. Then a list of entrances to that level appears, along with an indication in which direction the door points to (N, S, W, E). Be careful, you might end up impaled on the spikes in some places.  
  
```
map
```
```
map revealall
```
Should reveal all locations on the map. Note: might be buggy.  
  
```
restart
```
Reloads current level. This might lead to an amusing bug in which you can end up with multiple Penitent Ones (it persists only on the current level).  
  
```
sendevent
```
???  
  
```
show_debug_ui
show_debug_ui off
show_debug_ui on
show_debug_ui current
```
Seems to do nothing visible?  
  
```
showui
showui off
showui on
showui current
```
These commands toggle the UI - useful for screenshots. An interesting usage for this command is also trying to do a playthrough with UI turned off for added challenge.
--test the dialogs!  
  
```
skin
skin list
skin get
skin unlock SKIN_ID
```
These commands are related to player skins/palettes.  
  
```
testplan
```
???  
  
  
#### Statistic/attribute commands
```
bonus
bonus help
bonus list
```
The last of these commands shows current bonuses (for example, to strenght or sword power).  
  
```
fervour
fervour current
fervour set VALUE
fervour upgrade
fervour fill
fervour setmax VALUE
```
```
flask
flask current
flask set VALUE
flask upgrade
flask fill
flask setmax VALUE
```
```
health
health current
health set VALUE
health upgrade
health fill
health setmax VALUE
```
```
meaculpa
meaculpa current
meaculpa set VALUE
meaculpa upgrade
```
These commands are related to the power of the sword.  
  
```
maxfervour
```
Fills the fervour bar; it won't go beyond the limit set by guilt.  
  
```
purge
purge current
purge set VALUE
purge upgrade
purge fill
purge setmax VALUE
```
These commands are related to Tears of Atonement.  
  
```
skill
skill list
skill lock SKILLNAME
skill unlock SKILLNAME
skill showui
```
These commands are related to extra attacks unlocked in the Mea Culpa shrines.  
  
```
strength
strength current
strength set VALUE
strength upgrade
```
These commands are related to the strength of the Penitent One (no, really, imagine that).  
  
#### Item commands
Note the typo in `equiped`.  
```
bead
bead list
bead listowned
bead setslots SLOTS
bead add IDBEAD
bead remove IDBEAD
bead equip IDBEAD SLOT
bead unequip SLOT
```
These commands are related to rosary beads.  
  
```
collectible
collectible list
collectible listowned
collectible add IDCOLLECTIBLEITEM
collectible remove IDCOLLECTIBLEITEM
```
These commands are related to the collectible bones.  
  
```
prayer
prayer list
prayer listowned
prayer add IDPRAYER
prayer remove IDPRAYER
prayer equiped
prayer equip IDPRAYER SLOT
prayer unequip SLOT
prayer decipher IDPRAYER NUMBER
```
These commands are related to prayers.  
  
```
questitem
questitem list
questitem listowned
questitem add IDQUESTITEM
questitem remove IDQUESTITEM
```
These commands are related to various quest items.  
  
```
relic
relic list
relic listowned
relic add IDRELIC
relic remove IDRELIC
relic equiped
relic equip IDRELIC SLOT
relic unequip SLOT
```
These commands are related to relics.
