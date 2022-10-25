# Giants Editor - Hotkeys and Macros (GE-HAM): Script Reference


## Menus
The following command will activate (simulate a click on) any menu item in GE.
> **ActivateMenuGE**(mainMenu, *[subMenu1]*, *[subMenu2]*) 

* **mainMenu:** The name of the top level menu item (e.g. "Create")
* **subMenu1:** *(optional)* Name of the second level menu item (e.g. "Primitives")
* **subMenu1:** *(optional)* Name of the third level menu item (e.g. "Cube")

Examples

```ahk
F2:: ActivateMenuGE("File", "Import") ; Import a i3d object
F2:: ActivateMenuGE("Create", "Transform Group") ; Creates a transform group
F2:: ActivateMenuGE("Create", "Primitives", "Cube") ; Creates a cube
F2:: ActivateMenuGE("Create", "Primitives", "Cube") ; Creates a cube
``` 

## Scripts
The command *ActivateScriptGE* will execute any script within the "Scripts" menu.
> **ActivateScriptGE**(topLevelName, *[level2Name]*, *[level3Name]*) 

* **topLevelName:** The name of the folder or script at the top level in the "Scripts" menu (e.g. "Vehicles")
* **level2Name:** *(optional)* Name of the subfolder or script at the second level in the "Scripts" menu (e.g. "Dirt")
* **level3Name:** *(optional)* Name of the script at the third level in the "Scripts" menu (e.g. "Toggle Dirt")

Examples

```ahk
; Execute a script called "My Custom Script" located directly on the top level in the "Scripts menu"
F2:: ActivateScriptGE("My Custom Script") 

; Paint terrain by spline object
F2:: ActivateMenuGE("Terrain,", "Paint Terrain By Spline")

; Execute the script that increments scratches on vehicles
F2:: ActivateMenuGE("Vehicles", "Scratches", "Increment Scratches")
``` 


## Toolbar
To toggle any of the support (see below) toolbar buttons use the command *ToggleButton*.

> ToggleButton(buttonPresetName)

* **buttonPresetName:** The toolbar button preset name (e.g. `TB_PLAY`) of any support toolbar button, see below

### Toolbar button presets

- TB_PLAY
- TB_FIRSTPERSONMODE
- TB_LOCALWORLDMODE
- TB_SNAPPINGMODE
- TB_SCULPT
- TB_TEXTUREPAINT
- TB_MESHPAINT
- TB_INFOPAINT
- TB_FOLIAGEPAINT
- TB_TRANSLATIONMODE
- TB_ROTATIONMODE
- TB_SCALINGMODE


[<img alt="" height="250px" src="https://user-images.githubusercontent.com/7383510/194700763-9db317a3-98f6-4189-b496-9d061600742f.png?v_DATE" />](https://user-images.githubusercontent.com/7383510/194700660-9bd0ff03-a9b4-48a3-b961-2303a0b5d59c.png)


### Examples

```ahk
F2:: ToggleButton(TB_SCULPT) ; Activate the sculpt button with the F2 key
#F2:: ToggleButton(TB_ROTATIONMODE) ; Activate the rotation mode button with the Win+F2 key
``` 

## Navigation speed

### Set navigation speed to a fixed value

The following command will set the navigation speed to the desired level.
> SetNavSpeed(desiredSpeed) 

* **desiredSpeed:** The desired navigation speed (e.g. `1` or `50`)

***Important note:** Due to limitations in GE this command will first step the navigation speed to 1 and the increase the speed until the desired level is reached. To achieve this there is a soft limitaiton of 250 for the navigation speed. If you manually increase the speed above this soft limitaiton you might need to execute this command several times to actually reach the desired level.*

### Examples

```ahk
^NumpadMult:: SetNavSpeed(1) ; Will set the navigation speed to 1 when hotkey Ctrl+NumpadMultiply is executed
^NumpadMult:: SetNavSpeed(50) ; Will set the navigation speed to 50 when hotkey Ctrl+NumpadMultiply is executed
``` 

### Increment navigation speed in steps

The following command will increase the navigation in steps (supports negative numbers to decrease the speed).
> IncreaseNavSpeed(speedIncrement) 

* **speedIncrement:** The number of steps the navigation speed should be increased (or decreased if using a negative number)

### Examples

```ahk
; Increase the navigation speed by 10 when the Numpad Plus key is pressed while holding down Ctrl
^NumpadAdd:: IncreaseNavSpeed(10) 

; Decrease the navigation speed by 5 when the Numpad Plus key is pressed while holding down Ctrl and Shift
+^NumpadMult:: SetNavSpeed(-5) 
``` 

### Additonal commands *[WIP - unstable - not recommended to use]*

### Brush size
The following commands will cycle through a set of predefined brush sizes.

> CycleBrushSize()

> CycleFineBrushSize()

Both commands will cycle through a set of predefined brush sizes, however the `CycleFineBrushSize` will cycle through more sizes with smaller increments.

Default values used by `CycleBrushSize`:
> BRUSH_SIZES = [5, 10, 25, 50]

Default values used by `CycleBrushSize`:
> FINE_BRUSH_SIZES = [1, 2, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50]

These default values can overridden in your `GE-HAM_UserBindings.ahk` file like this:
```ahk
; Uncomment the lines below to use custom brush sizes
global BRUSH_SIZES = [8, 45, 200]
global FINE_BRUSH_SIZES = [1, 8, 25, 45, 100, 150, 200]
``` 
***Important note:** These two lines must be located above the line `#Include, %A_ScriptDir%\GE_HotkeysAndMacros.ahk` in your 'GE-HAM_UserBindings' file.*

### Brush geometry
The command `CycleBrushGeometry` will cycle between square and round brush.

> CycleBrushGeometry()

Example
```ahk
; Shift + F2 will toggle between round and square brush
+F2:: CycleBrushGeometry()
``` 
