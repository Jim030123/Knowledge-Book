![[Pasted image 20260408143820.png]]

- To drop a symbol to the editor sheet, need to first bring up the symbol chooser window.
- The symbol by searching for it or browsing for it.
- To bring up the symbol by searching for or browsing for it.
![[Pasted image 20260408144155.png|111]]


Choose Symbol Windows
![[Pasted image 20260408144408.png]]
1. Typing a few letters of its name in the search box or navigate the library and symbol list
2. Looking for the component symbol. The symbol chooser narrows down the contents of the listing pane.
3. Information about the selected symbol appears in the bottom left corner pane of the window. Some symbols also have associations with 1 or more footprints.
4. Using the drop-down menu and  verifying that have the correct association in the footprint preview pane。
5. I leave the footprint dropdown unchanged and click OK。
6. Dismiss the symbol chooser window, the symbol will be tied to the mouse cursor.
Delete the incorrect symbol by selecting it and hitting the "delete" key

![[Pasted image 20260408144212.png]]

Double click on the symbol to bring up its properties windows.
![[Pasted image 20260408152601.png]]

# Annotate
- Each symbol has a designator such as "D", "R" or "B1", followed by a question mark.
- Set the reference ID manually by editing the Reference field in the properties windows.
- Reference identifier is a unique name for this symbol that we can use in the schematic and the bill of materials as an identifier for The symbol.
![[Pasted image 20260409160317.png]]
- The question mark indicates that the designator for the symbol is not yet set.
![[Pasted image 20260408153314.png]]

![[Pasted image 20260408153344.png]]
# Associate
- What will this resistor look like in the final PCB.
- Defines the physical attributes of a component in the schematic diagram.
![[Pasted image 20260408153713.png]]
- The footprint Identifier in the footprint field, it is safer to click on the footprint library button to bring up the foot printer chooser windows.
1. Chooser to search and browse for the desired footprinted.
2. Double click to select it and associate it with the symbol when you find it.
![[Pasted image 20260408154624.png]]
# Assign footprint
- See the LED symbol already has an associated footprint.
- Can change on an alternative footprint from the right pane.
- Notice that as click on a symbol row in the middle pane.
![[Pasted image 20260408155001.png]]
![[Pasted image 20260408161142.png]]
- Right pane: will see a listing of all footprints in the selected library and match filter setting.
- Double click on the footprint: association appears on the symbol row in the middle pane to finish the association.
# Wiring
![[Pasted image 20260408161250.png]]
- When you use the hotkey, the editor will immediately start drawing a wire.
- To draw a new segment and change the drawing direction, click again.
- To finish drawing a wire, either double -click the cursor over the destination pin and left-click.
![[Pasted image 20260408162233.png]]
# Nets
![[Pasted image 20260408162307.png|144]]
- Representation of an electrical connection between 2 pins.
- You can see 4 wires that connect 4 pairs of pins,,
- To keep track of which pins are connected to which other pins.
![[Pasted image 20260408162607.png]]
- Have 2 wires that intersect and are electrically connected, both have the same name. Therefore it is possible to have nets that contain more than 1 wire.
- It is possible to give nets custom names so that is easy to identify. It is possible to some important nets such as those for the ground and operating voltage levels and signal nets.
## Electrical Rules Check
![[Pasted image 20260408162625.png]]
- To ensure that schematic does not contain errors that should be corrected before continuing with the layout workflow.
![[Pasted image 20260414154058.png]]
1. Clicking the Run ERC.
2. Clicking Violations and Messages tabs to switch between 2 types of output that the ERC can provide.
3. To use the checkboxes at the bottom of the window to enable or disable the various messages types.
135
![[Pasted image 20260408170701.png]]
![[Pasted image 20260408170706.png]]
![[Pasted image 20260408170726.png|358]]
![[Pasted image 20260409092907.png]]

![[Pasted image 20260409092725.png]]![[Pasted image 20260409092816.png]]