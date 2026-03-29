# NFS MW BNV Compiler - Blender Addon
NFS BB BNV Compiler is a Blender addon designed to prepare and compile vehicle geometry for Need for Speed Most Wanted 2005.

<img width="400" height="387" alt="Image" src="https://github.com/user-attachments/assets/09ad3928-74e5-41d2-9796-e2ee1b3620d5" />


- [How to use](#How-To-Use)

The addon automates multiple steps required in the BNV geometry pipeline, including object naming, material configuration, position marker creation, FBX export, and compilation using the BlackBox geometry compiler.


## Features
**Car Setup**
- Automatically rename objects with CARNAME prefix
- Remove prefix from objects if needed
- Prevent renaming of helper objects and markers

## Material Setup
- Automatically detects all materials in the Blender file
- Assign BlackBox shaders
- Supports custom shaders
- **Configure:**
  - Diffuse textures
  - Normal maps
  - Global textures
- Load existing materials.json
- Generate new materials.json
- Validation system to detect missing shader or texture inputs

## Position Marker Setup
Create and manage BlackBox position markers directly in Blender.
- Searchable marker list loaded from PositionMarkers.json
- Add markers with automatic numbering
- Remove markers safely
- Convert markers from Empty → Cube mesh
- Automatic rotation rules for specific markers:
  - HEADLIGHT → +90° X
  - BRAKELIGHT → -90° X
  - REVERSE → -90° X
  - EXHAUST → -90° X

# How To Use
## Step 1 — Prepare Car Name
Open the addon panel.
```
Car Setup
```
Enter the **Car Name.**
Example:
```
BMWM3GTR
```

## Step 2 — Rename Objects
Press:
```Rename Objects```
Objects will be renamed automatically:
```
KIT00_BODY_A → BMWM3GTR_KIT00_BODY_A
KIT00_HOOD_A → BMWM3GTR_KIT00_HOOD_A
STYLE01_HOOD_A = BMWM3GTR_STYLE01_HOOD_A
```
Position Markers starting with:
```
#LEFT_BRAKELIGHT
#RIGHT_HEADLIGHT
```
are ignored.


## Step 3 — Configure Materials
Open:
```
Material Setup
```
For each material:
1. Select a Shader or Enter Custom Shader
2. Enter Diffuse texture name
3. Enable Global Texture if needed
4. Enable Normal Map if required

Example:
```
Material: BADGING
Shader: DECAL
Diffuse: BADGING
Normal: BADGING
```
## Diffuse Texture Rules
By default, the addon automatically prefixes textures with the car name.
Example:
```
Diffuse input: BADGING
Generated JSON: BMWM3GTR_BADGING
```
## Global Texture Option
If Global Texture is enabled:
```
Diffuse input: BADGING
Generated JSON: BADGING
```
This removes the CARNAME_ prefix and allows the game to use global textures already present in the game files.
## Normal Map Rules
When entering a Normal Map name, you must not include _N manually.
Example input:
```
Normal: BADGING
```
The addon will automatically generate:
```
Generated JSON: BMWM3GTR_BADGING_N
```
If Global Texture is enabled for the normal map:
```
Generated JSON: BADGING_N
```


## Step 4 — Load Existing Materials JSON (Optional)
Click the folder icon in Material Setup.
Load:
```
materials.json
or
CARNAME.json
```
The addon will automatically apply the values to the matching materials in Blender.
If a material exists in Blender but not in the JSON, it will remain editable so you can configure it manually and create a new Material.json


## Step 5 — Create Position Markers
Open:
```
Position Marker Setup
```
1. Search and select a marker
2. Set the count [for example: 3]
3. Press:
```
Add Marker
```
Example:
```
#LEFT_BRAKELIGHT
#LEFT_BRAKELIGHT.001
#LEFT_BRAKELIGHT.002
```
Markers are created as Empty objects.


## Step 6 — Convert Markers
Once placed correctly:
```
Convert Empty to Cubes
```
Markers become small mesh cubes used by the game.


## Step 7 — Generate Materials JSON
Press:
```
Generate Materials JSON
```
This creates:
```
BNV/CARNAME/CARNAME.json
```


## Step 8 — Export FBX
Press:
```
Export FBX
```
File will be saved as:
```
BNV/CARNAME/CARNAME.fbx
```


## Step 9 — Update compile.bat
Press:
```
Update compile.bat
```
Paths are updated automatically.


## Step 10 — Compile Geometry
Press:
```
COMPILE
```
The compiler will generate:
```
GEOMETRY.BIN
```
inside the BNV/car folder.
If an output folder is selected, the file will be moved automatically.


## Output Folder (Optional)
You can specify a custom folder where the compiled file will be created.
Example:
```
Project/Release/
```
After compiling:
```
GEOMETRY.BIN → Output Folder
```


# Credits
- ASC
- ANILAG000
- Korchestroy3778
-  Galina Ivanovna


## License
This addon is provided for modding and educational purposes for Need for Speed BlackBox engine games.
