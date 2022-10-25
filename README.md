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
3. Review/edit your custom bindings by editing the file `GE-HAM_UserBindings.ahk` in a text editor of choice (examples included in the file)
4. Run `GE-HAM_UserBindings.ahk` by double clicking on the file
5. *(optional)* If you want to use *GE Hotkeys and Macros* together with *AutoHotPie* (radial menus) you need to follow some [additional steps](#Use-AutoHopPie-together-with-GE-HAM).

***Note:** See [GE-HAM Script Reference](REFERENCE.md) for details about all available commands in GE-HAM. For additional instructions about the key bindings, please see the [Hotkeys](https://www.autohotkey.com/docs/Hotkeys.htm) and [list of keys](https://www.autohotkey.com/docs/KeyList.htm) sections in the [AutoHotKey documentation](https://www.autohotkey.com/docs/Tutorial.htm).*




### Optional
* Install VS Code or Notepad++ as your text editor of choice
* If using VS Code is can strongly recommend the extension [AutoHotKey Plus Plus](https://marketplace.visualstudio.com/items?itemName=mark-wiemer.vscode-autohotkey-plus-plus)
* Create a windows shortcut to your `GE-HAM_UserBindings.ahk` and put that shortcut in your Start Menu Startup Folder to automatically start the script on every login

### Notes
* You can freely rename `GE-HAM_UserBindings.ahk` to any filename (or even create multiple copies) as long as the file `GE_HotkeysAndMacros.ahk` remains unchanged and in the same folder as your UserBindings file.


## Usage
To add your custom bindings edit the file `GE-HAM_UserBindings.ahk` and look for a section like this (default line 15):

```ahk
; \\\\\\\\\\ YOUR BINDINGS GOES BELOW THIS LINE //////////
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

### Use AutoHopPie together with GE-HAM
To be able to use GE-HAM macros via radial menus from AutoHotPie (and similar tools) you need to add the following section at the bottom of your `GE-HAM_UserBindings.ahk` file. 

```ahk
; \\\\\\\\\\ YOUR SPECIAL AUTOHOTPIE BINDINGS GOES BELOW THIS LINE //////////
#IfWinActive ; Below this line goes AHP bindings - do not edit this line
```

Then you need to bind the special command `AHPDummy()` for every GE-HAM command that you want to be able to call from AutoHotPie. Effectively you need to duplicate the keybinding, e.g:

```ahk
F2:: ToggleButton(TB_SCULPT) ; Original keybinding - can be used directly from GE

; \\\\\\\\\\ YOUR SPECIAL AUTOHOTPIE BINDINGS GOES BELOW THIS LINE //////////
#IfWinActive ; Below this line goes AHP bindings - do not edit this line

F2:: AHPDummy() ; Dummy to trigger F2 hotkey in GE from AutoHotPie
```

The first F2 binding is for the actual command to be executed in GE, either manually via the F2 key on your physical keyboard or indirectly via AutoHotPie. The second F2-bidning is to trigger the `AHPDummy()` command from any other program (e.g. AutoHotPie) which will act as an proxy and forward the F2 hotkey to GE (in this case toggle the sculpt button).

_**Important note:** to work around a limitation caused by AutoHotPie these special bindings could potentially be active in every program and not limited to GE (which is the case for all normal hotkeys). To avoid conflicts you could use obscure keybindings for selected AHP bindings, e.g. use `Shift+F24` even though your physical keyboard only got F-keys 1-12 (AHP and GE-HAM can still bind to F13-24)_


## Like the work I do?
I love to hear you feedback so please check out my [Facebook](https://www.facebook.com/w33zl). If you want to support me you can become my [Patron](https://www.patreon.com/wzlmodding) or buy me a [Ko-fi](https://ko-fi.com/w33zl) :heart:

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/X8X0BB65P) [![Support me on Patreon](https://img.shields.io/endpoint.svg?url=https%3A%2F%2Fshieldsio-patreon.vercel.app%2Fapi%3Fusername%3Dwzlmodding%3F%26type%3Dpatrons&style=for-the-badge)](https://patreon.com/wzlmodding?)


## Want to report a bug or have a great idea?
Please check out my [project page](https://go.xilent.se/wzl-modding-projects) to get more details about the my projects or post bug reports/feature requests. Here you will also find information about known issues, tips on workarounds and occationally also hotfixes.


## License

*GE-HAM © 2022 by w33zl is licensed under [CC BY-NC-ND 4.0](http://creativecommons.org/licenses/by-nc-nd/4.0/).*

*TL;DR: You are ALLOWED TO SHARE (copy and redistribute) the material in any medium or format as long as you ATTRIBUTE (give appropriate credit to) the original author, do NOT MAKE ANY DERIVATIVES (i.e. do not modify and re-publish this as your own work) and as long as it is NOT USED FOR COMMERCIAL PURPOSES.*

*EXCEPTION: You may freely distribute any changes and additions made to the 'GE-HAM_UserBindings.ahk' file (or copies thereof) without any restrictions.*
