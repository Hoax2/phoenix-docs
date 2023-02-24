# Building DA_ files in UE4

## Intro
How to get data from the game's DA JSON files back into UE4 quickly using Tangerie's scripts

**WARNING:** This is not for beginners

## Prerequisites

- [Custom PhoenixUProj UE4 engine](https://github.com/narknon/PhoenixUProj) <br>
Provides all the extra utilities and data types in the engine

- [Fmodel Dev Build](https://github.com/4sval/FModel/tree/dev) <br>
Latest versions allow you to export clean data.

### FModel Setup

1. Launch development build of FModel
2. Open `Settings > General > MapStructTypes`
3. Replace it with the [MapStructTypes JSON](/code/fmodel-MapStructTypes.json)

## Setup
- In command prompt navigate to the `Content` folder of your UProject
- Run `git clone https://github.com/Tangerie/Json2DA.git Python` 

## Use 
### Individual Asset Import
- Create a blank Data-Asset in the correct location for your mod with the correct name
  - Right-click > Misc > "Data Asset"
  - Select Parent Class to match "Type" in your JSON (`DA_GA_` this is "GearAppearanceItemDefinition") 
- Once done, right click your Data-Asset and select:
  - Scripted Actions > "Import Data Asset JSON"
- Copy and paste your JSON into this box, and hit "Ok"
- ! Your Data-Asset should now contain the correct structures


## Troubleshooting
First check the **Output Log** (`Window -> Developer Tools -> Output Log`). If the error is unclear, try creating all the required references manually (Textures, other assets, etc.), then reimport JSON
