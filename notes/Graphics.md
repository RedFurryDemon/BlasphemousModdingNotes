# Modding graphics

**Requirements:** GIMP, UABE  

## Uncompressing resource file
This may speed up load time. It is also needed for modding the resources.  

**Fair warning: as of version 2.0.22, the unpacked data file has the size of 3.97 GB. If you want to do asset modding, make sure you have at least 8-12 GB of available hard drive space.**

--1. Open UABE.  
--2. Go to `File->Open`. Open `data.unity3d`.  
--3. If the file is compressed, UABE will ask if you want to unpack it. Do so.  
--4. Save the uncompressed file under a different name.You might need to wait for a while until the decompression is finished.  
--5. Rename the original file to `data.unity3d.bak`.  
--6. Rename your uncompressed file to `data.unity3d`.  
--7. Run the game to check if it works fine with uncompressed assets.  


## Graphic replacers

This section describes the basic workflow with replacing a graphic asset for your own use. As an example, I am using my mod which replaces the screens that say `REQUIEM AETERNAM`, `DETESTATIO SACRORUM`, and `SUMMA BLASPHEMIA`. 
  
### Export  
  
--1. Open the unpacked `data.unity3d`.  
--2. Go to `Info` and wait until the processing is finished (might take a few seconds).  
--3. Find the assets you need. Make sure the type is `Texture2D`.  
Note #1:  
To get all textures, it's best to sort by type. (Thank you, Captain Obvious.)  
Note #2:  
Keep in mind that **alphabetical sorting in UABE puts lowercase and uppercase separately!**  
--4. Select the necessary assets.  
--5. `Plugins -> Export to .png`.  
--6. Save the file or select output folder (if extracting multiple files).  
  
### Editing
--1. Open the needed files in GIMP.  
--2a. If you're going to edit only the colors, go to `Windows -> Dockable dialogs -> Colormap`. Double-click the color you want to edit. When done, go to point 4.  
--2b. If you're going to alter the colors as well as the shape, first go to `Image -> Mode -> RGB`. Then edit the image like in point 3.  
--3. Use the "1 px" brush at 100% opacity for drawing and selection for erasing. Remember to **uncheck** `Antialiasing` and `Feather edges`. Delete using `del` or `Ctrl + X`.  
--4. Export the results as PNG files. Make sure they are indexed. If you've converted to RGB earlier, now convert back to Indexed. Let GIMP pick the optimal palette.  

### Import  
--1. Run UABE.  
--2. Open the uncompressed `data.unity3d` (`File --> Open`).  
--3. Click `Info`, then sort by name.  
--4. Select the texture (make sure it's of type Texture2D).  
--5. Go to `Plugins --> Edit`, then `Load`.  
--6. Pick your texture file.  
--7. `File --> save`, `Ok`.  
**Note:** this does not save the edit in the file yet!  
  
Now you can choose whether you want to create a mod installer, or just save the change in your data file.  
  
For an installer:  
--1. `File --> Mod maker --> Create standalone .exe installer`.  
--2. Fill the details. Note that you need to set up the correct game path, to the root folder. Example: `C:\Program Files (x86)\Steam\steamapps\common\Blasphemous`. Other users of this mod will be able to enter a different root folder path.  
--3. I don't recommend saving `data.unity3d` after having created an installer, because you'll need to test the installer anyway.  
  
For no installer:  
--1. `File --> Save`. UABE won't let you overwrite, so just save the file under a modified name.  
--2. Wait a longer while.  
--3. Swap the data file for the modified one and test the mod in-game.  

  