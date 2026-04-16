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
# Comments with text and graphics
- Can make software source more readable, annotations in an electronics schematic can improve the document's readability.
- Use the tools at the bottom of the right toolbar.
- Use the line tool to create a box around the circuit.
![[Pasted image 20260416122820.png]]
# Layout design
![[Pasted image 20260416123120.png]]
![[Pasted image 20260416123135.png]]
**PCB layout of this simple project contains several interesting elements:**
- Both surface-mounted and through-hole components.
- Rounded edges moulded around the footprints of the PCB components.
- Silkscreen graphics and text.
# Strat Pcbnew, import footprints
When import the schematic design from Eeschema, 2 primary elements of the design will appear in the editor:
- The component footprints.
- The nets that connect the footprint pins.
To importing the schematic design data, design process is also an opportunity to set up the editor.
1. Click on the Pcbnew button in the right pane
 ![[Pasted image 20260416123931.png]]

- Will use the importer tool. Can invoke  tool from the menu bar or the top  toolbar in PCBnew
![[Pasted image 20260416124151.png]]
- Importing data into an empty design editor, it doesn't matter what the status of the various options.
- Options are helpful when import and update from the schematic designer into the layout editor.
When import the new schematic data into an already populated layout editor, can ensure that KiCad will delete the footprint for the deleted symbol by enabling the "Delete footprints" in the importer tool window.

In this case, simply click "Update PCB" to populate the layout editor and Close to close the importer window.

![[Pasted image 20260416124756.png]]

- The thin "rat nest" that depict the nets or connections between the various pads of the footprints.
- Use the buttons in top part to do things such as add additional footprints to the editor or draw wires.
- Use the buttons in the middle of the right toolbar to draw graphics using the line, box and circle primitives.
- Use the buttons in the lower part of the right toolbar to measure distances between any 2 point of editor.
**Appearance group**
- Can choose the layer want to use. Most of work will be done in the front and back copper layer (B.Cu and F.Cu), the silkscreen layer (B.Silkscreen and F.Silkscreen) and edge cuts layer ("Edge.Cuts").

![[Pasted image 20260416125432.png]]
**Selection Filter**
- Allow to select the layout elements that the mouse cursor can select.
- Useful in busy layout where several elements overlap, making it challenging to select a specific one.
![[Pasted image 20260416125823.png]]

![[Pasted image 20260408170701.png]]
## Page Setting
- The information you enter will appear in the layout sheet information corner
![[Pasted image 20260409092907.png]]

![[Pasted image 20260408170706.png]]
![[Pasted image 20260408170726.png|358]]

# Outline and constraints (edge cut)
- How large would I like my project to be (This dictates the board's overall size and cost)
- How will I turn the LED on and off (This dictates the location of the button or switch)
- What is the biggest component of the board? (This dictates the shape of the board needed to accommodate the largest component)
**Constaints question that I asked myself**
1. LED torch should be large enough be large enough to hold in one hand and fit in my pocket easily. Arround 65mm in length and 25 mm in heigh should be sufficient.
2. I will use a small momentary button. I will be able to press the button with my thumb. When press button, the LED turn on.
3. The biggest component of the board is the  coin cell battery holder.
4. Will a 3D-printed enclosure. I will attach the LED torch board to the enclosure utilizing a screw, mounting bosses or slide-in-rails.
User.1 layers tab. The user layers allow to add text an d graphics that the manufacturer ignores.

Create a box with the approximate dimensions of my PCB and confirm that the footprint will fit within that space.
## Select the Edge.Cut layer
![[Pasted image 20260416142916.png]]
- Drawing rectangle with 66.29 mm X 26.41 height.
- The box tools selected, click to start following a rectangle and  drag the mouse until have reached the needed dimension.
- Outline can accommodate the footprints with much more to spare. Can decrease the height to reduce the overall size and cost PCB.
![[Pasted image 20260416142555.png]]
- Change the height of the outline that the board is thinner. Click on white outline to reveal the handles in the corners and middles of each lines.
![[Pasted image 20260416143850.png]]
- The handle in the middle of the top line to drag the line down. 
![[Pasted image 20260416144223.png]]
- Yellow front silkscreen: the battery footprints.
- Purple: The front layer
- White: user comment lines are partially outside the board outline
![[Pasted image 20260416145224.png]]
1. Click Edge.cut it in the layer tab to switch the active layer.
2. Select the line tool from the right toolbar.
3. Start drawing the first line from top right corner of the box.
4. I traced outline in the edge cuts layer until I had the entire board outline.
![[Pasted image 20260416145429.png]]
## Move footprint in place
- Emphasis on placing the footprints that have a user interface or important functional role first and then continue with the rest.
- The layout editor provides visual clues about the routes by showing the pad-to-pad connections using the "ratnest" lines. Fewer overlapping ratnest lines will result in a cleaner and easier to draw a network of routes.
**Overlapping ratnest lines**
- Reducing the number of overlapping ratnest lines help reduce the complexity of the route network in the next step of the workflow.
![[Pasted image 20260416152146.png]]
**Questioning**
1. Is the placement of the footprints complete?
2. Is there anything else I can do improve this board before continuing with the routing step.
![[Pasted image 20260416152347.png]]

# Route
- Thin ratnest line will  guide through the routing process. The routing is complete when all ratnest have been replaced by copper routes.
![[Pasted image 20260416152605.png]]
- All ratnest lines are grey-white, except for one that is green.
- Select "Route tracks tool", the cursor becomes a pen.
- Advantage of starting the drawing process from a pad is that the ratnest line guide to the route's destination. I will start drawing from pad 2 of R1.
![[Pasted image 20260416154059.png]]
- Can define the geometry of the route, such as its corners and angle. When move the mouse pointer over the destination pad, will notice the snap effect.
![[Pasted image 20260416154208.png]]
- Once have drawn a route, it is possible to modify it by dragging its component, can also delete it and re-draw it.
- Click on track segment 'D' (45 degree angle) or 'G' (free-angle) choose the type of move option want.
## Config board
- Can configure a different a different set of copper layers if you wish. Go to File, Board Setup, use the drop-down menu to select the number of copper layers for board.



![[Pasted image 20260409092725.png]]![[Pasted image 20260409092816.png]]
## Design Rule Check (DRC)
1. DRC window by clicking on the DRC in the top toolbar, clicking on the DRC button in the top toolbar and click on Run DRC.
2. Not routing error and can fix it in the workflow.

## Refine the Outline
- Will refine the board outline as now all the footprint are in place.
![[Pasted image 20260416155433.png]]
>[!note] Make changes that implement the following
>- Reduce the total size of the board to a minimum.
>- Replace the angle corners and rounded corners.
>- Enclose the battery footprint within the PCB outline using 2 rounded segment for the top and bottom parts of the footprint.


>[!note] Arc hard to connect
> When the arc and top line meet, click again to finish the drawing. The arc is complete. Could not connect the bottom end of the semicircle to the bottom horizontal line.
> 
> To fix this, select the bottom horizontal line and move it down that it touches the end of the semicircle. Need to "play" with the position of the lines involved and the grid and grid size that can perfectly connect the outline segment.
> ![[Pasted image 20260416160554.png]]
> 

![[Pasted image 20260416160611.png]]
- More careful with my drawing, before making any changes in the Edge.Cut layer.
- Will use the User.2 layer to draw a guide circle. This circle will help me draw the correct arc in the Edge.Cuts layer.
![[Pasted image 20260416161055.png]]

![[Pasted image 20260416161417.png]]
1. Move the cursor towards the location where the blue circle intersects the edge cut line on the left side of the battery holder. Click When you see a small circle that indicates the intersect.
2. Continue to draw the arc towards the left side until the arc intersects the edge cuts line on the right side.
![[Pasted image 20260416161840.png]]

3. Click on the line to reveal the handle on the right side and use the handle to resize the line.
4. Using the line tool, create a new line that starts at the right end of the arc.
5. Connects with the top end of the right vertical line.
>[!note] 0.254mm to draw a rounded edge
>- Keeping an eye on the dx/dy values of the status bar.
>- Place the cursor on the corner and press the space bar. The space bar press will reset the dx/dy distance counters to 0.
>- Move the mouse pointer diagonal down and left so that that dx and dy are both showing 1.27mm.
>![[Pasted image 20260416163904.png]]
>- Position and distance from the corner will produce the arc that want.
>- Click to start drawing the arc, then move the mouse to touch the horizontal line and click again to define the radius. Then drag toward the right and down to intersect the vertical line and click to finish the drawing.
![[Pasted image 20260416164514.png]]
![[Pasted image 20260416164550.png]]

![[Pasted image 20260416164600.png]]
# Silkscreen
**Front**
- Will add informative and decorative text and decorative text and graphics in the front and back silkscreen layers.
- Change the layer of the LED text label to F.Silkscreen.
- Click OK to commit the change and notice the "LED" label is now yellow
![[Pasted image 20260416165024.png]]

**Back**
![[Pasted image 20260416165157.png]]
- Click on the text tool from the right toolbar and click just below the logo to bring up the properties window.
![[Pasted image 20260416165624.png]]
![[Pasted image 20260416165640.png]]
## Design rule check
![[Pasted image 20260416165804.png]]
- The warning indicates that the reference designator for the logo footprint contain "\*" at the end of its name and therefor is undefined.
![[Pasted image 20260416170015.png]]
- Notice that the reference designator  is REF change this to REF1, which is unique on this board.
**3 option to solve**
- Go back to the schematic editor, add new symbol and associate it with the logo footprint
- Ignore this warning
- Open the footprint's properties and check the checkbox "Not in schematic"
![[Pasted image 20260416170510.png]]

# Export Gerbers and order
- Pcbnew support Gerber files export as 1 of its fabrication outputs. 
![[Pasted image 20260416170738.png]]

![[Pasted image 20260416170827.png]]
- Click the plot. Output message box, will see confirmation that the Gerber files are created.
- Will generate the drill files, which contain information about through-holes and vias. Click on "Generate Drill Files".
## For the manufactures
- Ask that compress the Gerber files directory as a ZIP file and upload the ZIP file.
![[Pasted image 20260416171357.png]]
## Gerber viewer
![[Pasted image 20260416171538.png]]
![[Pasted image 20260416171542.png]]
1. Click on "Gerber Viewer"
2. In Gerbview, go to the file and click on "Open Gerber Plot" 