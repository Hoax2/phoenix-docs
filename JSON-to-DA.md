# Building DA_ files in UE4

## Intro
How to get data from the game's DA JSON files back into UE4 quickly using Tangerie's scripts

**WARNING:** This is not for beginners

## Prerequisites

- [Custom PhoenixUProj UE4 engine](https://github.com/narknon/PhoenixUProj) <br>
Provides all the extra utilities and data types in the engine

- [Fmodel Dev Build](https://github.com/4sval/FModel/tree/dev) <br>
Latest versions allow you to export clean data. The old builds skip things.<br>OR<br>
A copy of your `DA_GA` JSON file that was extracted using this build.

### FModel Setup

1. Launch development build of FModel
2. Open `Settings > General > MapStructTypes`
3. Replace it with the [MapStructTypes JSON](/code/fmodel-MapStructTypes.json)

## Setup

- Create `Content/Python` folder in your project folder
- In windows add [Tangerie's scripts](https://github.com/Tangerie/Json2DA) to this folder
- Create a "Editor Utility Blueprint" with the parent class of "AssetActionUtility" 
    - In UE4: Right-click > Editor Utilities > "Editor Utility Blueprint"
    - Name it "import_gear_json"
- Create your blueprint in [this structure with this script](https://blueprintue.com/blueprint/tth-x8_1/)
    - in the left-panel add a function, name it "Import Data Asset JSON"
    - with that node selected in the right-panel add Input "JSON" as String
    - string together the blueprint
    - Save, Compile

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
