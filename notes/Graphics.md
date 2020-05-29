## Graphic replacers  
**Requirements:** Gimp, UABE  
--write how to use UABE  
  
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
4. Side note: While editing `REQUIEM AETERNAM`, I also noticed that the different shades of orange look bad without the background, so I decided to use only one shade. However, it turns out only the `AE` is problematic (I checked by selecting by color the main part of the text, and the alpha background - 2 clicks with treshold 0, and then inverted the selection to see which parts had anything other than these two colors). I ended up simply editing that letter by hand, using 1-pixel brush.  
  
Before and after (selection to show edited parts):  
![image editing](images/Modding_graphic_shades_01.png)  
5. One more side note: Then I decided to slightly alter the color of `SUMMA BLASPHEMIA` text to add some more blue. This can be done for example by editing the color palette. Go to `Windows -> Dockable dialogs -> Colormap`. Double-click the color you want to edit. I changed it from `#ca439f` to `#8943ca`.  
  
Palette editing in GIMP:  
![palette editing in GIMP](images/Modding_graphic_colormap_01.png)  
6. Save the .png files in `Modding_Graphics_Import` and put them in the game assets using UABE.  
  
--graphic replacer (sprite change - example: flying head -> skull)  
