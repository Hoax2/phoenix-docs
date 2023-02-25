# Building DA files in UE4

## Overview
> Outlines how to get data from the game's DA JSON files back into UE4 quickly using Tangerie's scripts.


**WARNING: This is not for beginners!**

Appearance skins for clothing use `GearAppearanceItemDefinition` DataAsset (DA_GA) files to define the textures and color overrides for the model. These files also define the color and texture overrides for each house. To change them you need to:
1. Export clean DA_GA JSON from the game's Pak files
2. Rebuild the JSON data as a DataAsset in UE4 (using scripts)
3. Then you can edit them in UE4 to make your changes for mod-packaging 

## Prerequisites

### [Custom PhoenixUProj UE4 engine](https://github.com/narknon/PhoenixUProj) <br>
Provides all the extra utilities and data types in the engine

### [Fmodel Dev Build](https://github.com/4sval/FModel/tree/dev) <br>
Latest versions allow you to export clean data.

#### FModel Setup:

1. Launch development build of FModel
2. Open `Settings > General > MapStructTypes`
3. Replace it with the [MapStructTypes JSON](/code/fmodel-MapStructTypes.json)

## Setup
Add [Tangerie's scripts](https://github.com/Tangerie/Json2DA) to a `/Content/Python` folder using Git:
1. In command prompt navigate to the `/Content` folder of your UProject
2. Run `git clone https://github.com/Tangerie/Json2DA.git Python` 

## Process 

### 1 - Get the DA JSON data
Using the correct version of Fmodel, find the DA_GA file you want to replace, then export the JSON.
```
Phoenix/Content/Data/GearAppearances/
```
**Tip:** Finding the correct DA_GA can be difficult, you can use the images in `Phoenix/Content/UI/Icons/Gear` to identify the gear ID.


### 2 - Individual Asset Import
1. Create a blank Data-Asset in the correct location for your mod with the correct name
    * Right-click > Misc > "Data Asset"
    * Select Parent Class to match "Type" in your JSON (`DA_GA_` this is "GearAppearanceItemDefinition") 
2. Once done, right click your Data-Asset and select:
    * Scripted Actions > "Import Data Asset JSON"
3. Copy and paste your JSON into this box, and hit "Ok"
4. ! Your Data-Asset should now contain the correct structures


## Troubleshooting
First check the **Output Log** (`Window -> Developer Tools -> Output Log`). If the error is unclear, try creating all the required references manually (Textures, other assets, etc.), then reimport JSON
