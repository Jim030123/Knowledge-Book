# Left Toolbar
![[Pasted image 20260415161331.png]]
## Grid lines
![[Pasted image 20260415163014.png]]
- Allows to enable or disable the editor's grid lines.
- The schematic editor can display the grid in 3 styles: lines, dots and small crosses.
![[Pasted image 20260415161746.png]]
- Zoom in and out using mouse scroll wheel, the grid automatically adjusts.
- Can change the size of the grid size,.
- Can Right-click anywhere in the editor window to open the context menu, then select Grid to open the submenu and then select 1 the available grid sizes.
![[Pasted image 20260415162006.png|450]]
- Can always check the current grid side in the status bar at the bottom of the Eeschema window.
- Can choose inches, millimetres and mil.
![[Pasted image 20260415163033.png]]
![[Pasted image 20260415162038.png]]

## Cursor

- Change the shape of the cursor by clicking button "3" in the left toolbar.
![[Pasted image 20260415162401.png]]
- Full-window crosshair variant makes it easier to compare  the cursor's position against other objects in the designer window and makes it easier to align object.
## Display hidden pins
![[Pasted image 20260415163428.png]]
![[Pasted image 20260415162630.png]]
- Contain hidden pins to reduce clutter in the editor.
- Pin 21 is set as "hidden".
## H & V lines
![[Pasted image 20260415163054.png]]
- Allow to draw wires and busses that connect pins.
- The editor restricts these lines to horizontal or vertical. If you disable the tool, can draw these lines at any angle you want.
![[Pasted image 20260415163846.png|697]]

# Top toolbar overview
![[Pasted image 20260415163933.png]]
 
## Save
![[Pasted image 20260415164223.png]]
- Click save to work on the disk.
## Schematic Setup
![[Pasted image 20260415164417.png]]
- Gives you access to the Schematic Setup window. Can customize the schematic editor to match work style and project requirement.
- Set the default text size for text labels, create field name templates.
- Customize how the electrical rules checker works.
![[Pasted image 20260415164402.png]]
## Page Settings
![[Pasted image 20260415164551.png]]
- Allow to configurate the schematic editor page
- Can choose the size of the schematic editor page then set contents of sheet label that appears in bottom right corner of the page.
![[Pasted image 20260415164637.png]]

## Print and Plot
![[Pasted image 20260415165132.png]]
- Allow to print or plot schematic. Difference between 2 options relates to where the printing will take place.
**Print**
![[Pasted image 20260415165145.png]]
Allows to print the schematic to paper on a regular printer.

**Plot**
![[Pasted image 20260415165203.png]]
Allows to export the schematic to a file using 1 of the available file formats:
- Postscript
- PDF
- SVG
- DXF
- HPGL

## Paste from clipboard
![[Pasted image 20260415165518.png]]
- Copy a selected item to the clipboard that can paste it somewhere else in the editor.
1. First click on any element to select it.
2. Ctrl + C on keyboard.
3. To Paste Ctrl + V on keyboard.

## Undo and Redo
![[Pasted image 20260415165541.png]]
**Undo**
To revert the last change you made.

**Redo**
To Redo it.

## Find
![[Pasted image 20260415165655.png]]
- To search for a string of text anywhere in the schematic editor.
## Find and Replace
![[Pasted image 20260415165753.png]]
- Allows to change the matching text to a new text string. 
## Navigation Buttons
![[Pasted image 20260415165910.png]]
1. Refresh
2. Zoom In
3. Zoom Out
4. Zoom to Fit (Ctrl + 0)
5. Zoom to Objects (Ctrl + Home)
6. Zoom to Selection (Ctrl + F5)

Click on the Zoom to Selection button then use mouse a rectangle contains the details at which want to take a closer look.
![[Pasted image 20260415175140.png]]
## Sheet hierarchy
![[Pasted image 20260415175241.png]]
- First sheet is the "root" and may contain 1 or more sheets. Subsequent sheets may have sub sheets.
- When are in a sheet other than "root", can click on the Up arrow button to jump up to the previous sheet.
## Rotate and Flip
![[Pasted image 20260416092322.png]]
Allow you to rotate or flip the currently selected element:
- Rotate by 90 degrees
- Rotate by -90 degrees
- Flip vertically
- Flip horizontally
**Applied the vertical flip operation to the 4020 symbol**
![[Pasted image 20260416092040.png]]
Left:  Original orientation
Right: Flipped version

## Symbol editor
![[Pasted image 20260416093707.png]]
- Can edit existing symbols or create new one.
![[Pasted image 20260416093415.png]]
## Symbol libraries browser
![[Pasted image 20260416093750.png]]
- Allows to find a symbol and add it to the schematic editor sheet.
- Once you select a library, its contained symbols appear in the middle pane of the window.
![[Pasted image 20260416093936.png]]
## Footprint Editor
- Allows to edit or create footprints.
![[Pasted image 20260416094123.png]]
## Annotate Schematic
![[Pasted image 20260416094405.png]]
- Allow to quickly create and assign reference designator to all symbols in schematic.
- Can set designators manually, it is better to leave this task to the automated tool for all practical purposes.

![[Pasted image 20260416094412.png]]

## Electrical Rules Checker (ERC)
- That finds violations in the schematic.
- It can find pins left unconnected or power pins not connected to a power source.
- Possible to customize how the ERC tool works and fine-tune it t the requirements of project.
![[Pasted image 20260416094651.png]]
## Assign footprint
![[Pasted image 20260416094931.png]]
- Must be associated with footprints that will appear in the layout editor.
- Doing it this way is tedious and time-consuming. A better way is to use the bulk associations tool available from the top toolbar.
![[Pasted image 20260416095211.png]]
Left pane: Contains the available footprint libraries
Right pane: Contains footprints that match search filters have selected.

## Bulk-edit symbol fields
![[Pasted image 20260416095913.png]]
- Across all schematic symbols is to use the bulk symbol field editor.
- Can use this tool like a spreadsheet.
- To commit changes and close the window.
- Click on the "Apply, Save, Schematic & Continue"
- Helpful if want to create a BOM (Bill of Material)
![[Pasted image 20260416095906.png]]
## Bill of Materials
![[Pasted image 20260416100126.png]]
- A list of the components needed for printed circuit board, including information like quantitied, values and sources.
## Pcbnew
![[Pasted image 20260416100301.png]]
- Open the layout editor.
## KiCad Python shell (Deprecated)
- Can use to add functionality in Python modules or interact with KiCad directly using Python commands and KiCad's Python API.
# Right toolbar
![[Pasted image 20260416100750.png]]
## Pointer
- When no tool is active, you are using the default pointer.
- If have activated a tool, can revert to the pointer by clicking on the arrow button or hitting the escape key.
- Can left click on any element in the designer to select it and can use a hotkey, right click to show the context menu or click and hold to move it.
## Net and pin highlighter
![[Pasted image 20260416101704.png]]
- That makes it easy to see wires and pins that belong to the same net.
- Click on the highlighter button and click any wire or pin that belongs to the net want to highlight.
![[Pasted image 20260416101724.png]]
## Symbol Chooser
![[Pasted image 20260416102521.png]]
- Used the symbol chooser window to browse the available libraries.
![[Pasted image 20260416102445.png]]
Right side: Can see the symbol in the preview pane.
- Also has an associated footprint, which can also see in the right bottom pane.
- 2 preview panes, there is a footprint dropdown.
- Many symbols have more than 1 compatible footprint and use this dropdown to select the most appropriate footprint for project.
## Power symbol chooser
- A specialized version of symbol chooser. Can quickly find and add power-related symbol in the preview pane on the right of this window.
- Invoked the power symbol chooser and have selected the +3.3VA symbol.
- Power symbol don't have associated footprints because they don't have a physical representation on the final PCB.
- Uses the power symbols during ERC to determine whether power pins are correctly wired.
**Example**
- Imagine a symbol, such as microcontroller that contains a pin configured as a power pin. If this pin is not connected to a compatible power symbol, the ERC will report this as violation.
## Wire 
- Enable the wiring the witing tool can draw wires that connect pins.
- The wire tool is automatically enabled that you can start drawing a new wire. Place the cursor over the pin circle and lick, the drawing ends.
Click: To draw a wire, click on its button to enable the wire tool and left click anywhere in the editor to start drawing. Click again to create an angle and continue drawing.

Double Click: End drawing.
![[Pasted image 20260416105430.png]]
## Bus


