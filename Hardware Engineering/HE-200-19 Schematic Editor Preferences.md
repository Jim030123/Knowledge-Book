- Use its configuration options to set up KiCad to suit work style and project requirement.
![[Pasted image 20260417091533.png]]

# Display option:
## Grid Options
- How the grid looks and works.
- Set the grid style (dots, lines, crosses), thickness, minimum spacing, enable /disable snap to grid.
- Keep snap-to-grid always enabled to help me position the various elements in the editor and draw the wires.
## Cursor Options
- The shape of the cursor.
- Allows to switch between small and full window crosshairs.
## Appearance
- The appearance of hidden pins and fields.
- Allow to choose default settings for the hidden pins and fields,
**Hidden pin showing and hiding**
![[Pasted image 20260417092712.png]]
## Selection
![[Pasted image 20260417093258.png]]
- How selection works.
- Set the appearance of single or a group of elements selected with the mouse.
- With Fille Selected checked, will fill the resistor's symbol with the highlight color.
## Cross-probing
- How cross-probing works.
- That links the schematic symbols to their layout counterparts.
- If any cross-probing options are enabled, clicking on symbol will pan the layout editor to bring the associated footprint in view.
![[Pasted image 20260417093654.png]]
- Clicking on a symbol will pan the layout editor to bring the associated footprint in view.
- Schematic editor will pan and zoom on the symbolic counterpart.
**Cross-probing group checked that when I click on an element in Pcbnew:**
- Pan the view to center on the to associated symbol
- Zoom in
- Highlight the symbol
# Edit Option
- Repeated Item group controls  useful and time-saving behaviours. 
![[Pasted image 20260417094648.png]]

**Example**
- 4 pins or wires. Want to use net labels to connect them to other pins.
- To create 4 labels and attach them to the wires manually or Use the "repeated item", can create the first label, say "net_1" and attach it to the first wire.
![[Pasted image 20260417095115.png]]
- Can repeat the last action and have the editor create and attach the remaining labels automatically (Shift + L).
![[Pasted image 20260417095211.png]]
- 3 of the labels were created and placed by the schematic editor.
- The labels must finish with a number that the auto-numbering can work and place of the wires must be equal to the vertical pitch specified in the  "Related item".
## Colours
- Select "New Theme" from the drop-down menu.
- Give theme a name and then click on the colour box of the element that want to change. Select color and click OK.
![[Pasted image 20260417100535.png]]

![[Pasted image 20260417100403.png]]
![[Pasted image 20260417100720.png]]
# Field name template
- Can add custom fields to the list of symbol field properties and complement the pre-defined ones.
![[Pasted image 20260417101123.png]]
- The search filter. Type in text to match symbols based on their name or keywords.
- The library browser. Tool contains a hierarchy of symbol library. Click on the greater-than symbol (">") to expand it and reveal the symbols contained within it.
- When select a symbol in the library browser, the symbol information will appear in the information pane.
- Schematic symbol preview
- List compatible footprint. Many symbol have list of footprints dropdown, will see the footprint's preview.
- Show the Symbol Browser Window. This window provides an alternative method to find a symbol.
- Place repeated copies. With this checkbox selected, can add multiple copies of the same symbol to the sheet. Find and choose the symbol want to add. Then, repeatedly click on the schematic editor sheet to place multiple copies of the same symbol.
- Place all unit. If a symbol contains more than 1 unit, checking the "Place all unit" will units to the schematic sheet.
![[Pasted image 20260417102420.png]]
**The Difference between Library Browse and Symbol Chooser**
1. The browser does not have a filter field, you have to navigate using the library and symbol panes.
2. Contain more than 1 unit are accessible via a drodown menu in the Browser and the library and symbol hierarchy pane in the chooser.