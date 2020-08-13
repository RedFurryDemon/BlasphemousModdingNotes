# Palette editing 
**Requirements:** GIMP, UABE  
  
### Preparations  
The basics of graphic modding are described [here](Graphics.md).  

Download my .psd file for live palette preview (mainly for a brand new palette or editing the default one), or export one of the palettes from `data.unity3d`. Or both.  

List of skins with their palettes:  

```
PAL_Penitent_ORIGIN - Default Appearance
PAL_Penitent_ALT - Son of The Miracle
PAL_Penitent_ALT2 - True Apostasy
PAL_Penitent_ALT3 - Warden of the Ossuary
PAL_Penitent_ALT4 - Golden Burden
PAL_Penitent_ALT5 - Alloy of Sin
PENITENT_ALMS - Alms for Oblivion
PENITENT_PE01 - [unlocked after completing NG+ with the Penitence of the Unwavering Faith]
PENITENT_PE02 - [unlocked after completing NG+ with the Penitence of the Bleeding Heart]
PENITENT_PE03 - [unlocked after completing NG+ with the Penitence of the True Guilt]
```

### Using RFD's palette preview file
--1. Open `palette_preview.psd` in GIMP.  
--2. Adjust color of the layers to your liking using `Colorize`, `Hue/Saturation`, or `Values`. Don't draw on the image.  
--3. `Image --> Flatten image`.  
--4. Crop the image to only have the palette (exactly 256 x 1 px).  
--5. Conver the image to indexed mode and export as a .png.  
--6. Import into game data or create a mod installer.  

### RFD's description for UABE skin mod installers

Up for grabs if you're too lazy to write your own.  

```  
This mod replaces the [skin name] skin in Blasphemous.

The installer affects the file data.unity3d in Blasphemous/Blasphemous_Data; there is no need to backup the original file because the installer does that automatically. However, if you prefer to create an additional backup on your own, feel free to do so before you proceed.

During the installation, make sure to provide the path to the root Blasphemous folder, not the data folder.
Example:
C:\Program Files (x86)\Steam\steamapps\common\Blasphemous

Keep in mind that this mod will not unlock the skin automatically, you need to obtain it by regular means.


Sorrowful be the heart, Penitent One.
```
  
