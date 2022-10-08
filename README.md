<<<<<<< HEAD
# Giants Editor - Hotkeys and Macros (GE-HAM)

Tired of endlessly clicking in the menus and toolbar in Giants Editor and wishing there were more hotkeys/keyboard shortcuts? Now there is! With this AutoHotKey library you can bind a lot of common actions in GE to keyboard or mouse shortcuts or even create multi-step macros. If you want to take things one step further, you can also combine this with AutoHotPie (or any other radial/context menu of choice).


## Main Features
* Fully customizable hotkeys/keyboard shortcuts and macros
* Execute user scripts
* Execute menu actions
* Toggle most toolbar buttons on/off
* Change navigation speed
* Change brush size and geometry
* And more to come...

### Preview
Note how the different toolbar buttons get activated/toggled without the mouse is moving. This is just one of many use cases for this script.
![C5dal7m4VI](https://user-images.githubusercontent.com/7383510/194701227-d5095d81-da26-4b65-9a50-661176d17b22.gif)


## Getting Started

1. Download and install AutoHotKey ([www.autohotkey.com](https://www.autohotkey.com/download/ahk-install.exe))
2. Download this package and unzip to any suitable folder
3. Add your custom bindings by editing the file `GEUserBindings.ahk` in a text editor of choice (examples included in the file)
4. Run `GEUserBindings.ahk` by double clicking on the file

***Note:** See [GE-HAM Script Reference](REFERENCE.md) for details about all available commands.*


### Optional
* Install VS Code or Notepad++ as your text editor of choice
* If using VS Code is can strongly recommend the extension [AutoHotKey Plus Plus](https://marketplace.visualstudio.com/items?itemName=mark-wiemer.vscode-autohotkey-plus-plus)
* Create a windows shortcut to your `GEUserBindings.ahk` and put that shortcut in your Start Menu Startup Folder to automatically start the script on every login

### Notes
* You can freely rename `GEUserBindings.ahk` to any filename (or even create multiple copies) as long as the file `GiantsEditorShortcuts.ahk` remains unchanged and in the same folder as your UserBindings file.


## Usage
To add your custom bindings edit the file `GEUserBindings.ahk` and look for a section like this:

```ahk
; ::[ GENERIC GIANTS EDITOR BINDINGS ]::
``` 

Below this line you add your bindings in the format `{HOTKEY}:: {COMMAND}` (i.e. first the hotkey, then double-colon and lastly the command to execute). Example to toggle the brush toolbar button with the F2 key:

```ahk
F2:: ToggleButton(TB_SCULPT) ; Activate the sculpt button with the F2 key
``` 

### Additional basic examples
```ahk
^t:: ActivateMenuGE("Create", "Transform Group") ; Ctrl+T will create a transform group
F4:: ActivateScriptGE("My Custom Script") ; F4 will execute a script called 'My Custom Script'
^NumpadMult:: CycleBrushSize() ; Ctrl+NumpadMultiply will cycle between a number of predefined brush sizes
``` 


### Advanced example
Besides simple one-line single command hotkey it is also possible to define multi step macros like this:

```ahk
; Create a cube AND trigger the interactive placement command (with one shortcut)
+^t:: ; Ctrl+Shift+T
    ActivateMenuGE("Create", "Primitives", "Cube")
    ActivateMenuGE("Edit", "Interactive Placement")
return
``` 

**Important note:** it is mandatory to end the multi-line macro with a `return` statement.
=======
# Giants Editor Hotkeys and Macros (GE HAM)
>>>>>>> parent of 29a08a5... Initial GE-HAM reference documentation

DESCRIPTION

## Like the work I do?
I love to hear you feedback so please check out my [Facebook](https://www.facebook.com/w33zl). If you want to support me you can become my [Patron](https://www.patreon.com/wzlmodding) or buy me a [Ko-fi](https://ko-fi.com/w33zl) :heart:

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/X8X0BB65P) [![Support me on Patreon](https://img.shields.io/endpoint.svg?url=https%3A%2F%2Fshieldsio-patreon.vercel.app%2Fapi%3Fusername%3Dwzlmodding%3F%26type%3Dpatrons&style=for-the-badge)](https://patreon.com/wzlmodding?)


## WHATISRELEVANT
* TBD

## Want to report a bug or have a great idea?
Please check out my [project page](https://go.xilent.se/wzl-modding-projects) to get more details about the my projects or post bug reports/feature requests. Here you will also find information about known issues, tips on workarounds and occationally also hotfixes.
