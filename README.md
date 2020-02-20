# Folding AngleBarLamp

Folding lamp made out of 3d-printed parts and anglebars. Inspired by the lamps from [kliments workshoptoolset](https://github.com/kliment/workshoptoolset)


![folding animation](images/angleBarLamp.png "")

The lamp parts were designed using Freecad 0.19 and the [assembly4 workbench](https://github.com/Zolko-123/FreeCAD_Assembly4).

## Printed parts

### TopBlock
![folding animation](images/topBlock.png "TopBlock")

### BottomBlock
![folding animation](images/bottomBlock.png "BottomBlock")

### CableClips
![folding animation](images/cableClip.png "CableClip")

## Other parts

### Screws:
##### topBlock
  * 2x M3x16
  
  or
   
  * 2x M3x18 + 2x M3 Washers & 2x M3 Nuts
      
##### COB LED attachment
  * 4x M3x10

### angle bars for arms and foot (length can be modified to suit needs):
  * 2x  8mm x 400mm
  * 2x 10mm x 400mm

### Electronics:
  * 2x COP LEDs that suite your needs
  * Power supply
  * Switch or dimmer (check workshoptoolset)
  * 2x 1.5m wire
## Folding Mechanism
![folding animation](images/foldingAnimation.gif "Folding mechanism")

### Running the animation in FreeCAD

* Open the assembly4 workbench
* Run "Animate Assembly" with these parameters


![animation parameters](images/animationParameters.png "")

### Background

This assembly is a bottom-up design (no master sketch), mostly because I already had created some of the parts prior to using assembly4.

Parts are attached using features on the bodies as reference for LocalCoordinateSystems. For the moving parts these refernces are mostly circular reatures with **Concentric** attachment mode (i.e. **LCS_armRight** in **p_topBlock**).

The other LCSs are attached in **XY tangent to surface** mode using a face and a vertex on that face as references. In some cases where a vertex in the right position was not available x & y offsets were used (i.e. **LCS_connector10mm_lower** in **bottomBlock**)

Animation is controlled by the **time** variable. Nested conditional statements execute the different parts of the motion as the **time** variable is incremented. This way rotation und position parameters of the arms are calculated in the attachment section of the **LCS_screwhole** in **Parts/p_angleBar_8mm_arm**. To keep the expression managable some intermediate variables are calculated in **Model/Variables**.
