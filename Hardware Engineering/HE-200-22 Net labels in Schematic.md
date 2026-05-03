- Avoid using wire and bus lines, resulting in less cluttered and better-looking schematic.
- Create nets with custom names that can recognize in the schematic and layout editor.
- Layout editor depicts the nets with thin ratnest lines.
- Create a net label and attach it to one of the wires in the schematic editor.
- Net label button in the right toolbar.
![[Pasted image 20260417144025.png]]
**Example**
![[Pasted image 20260417150104.png]]
- Used net labels to electrically connect several pins of the U1 symbol tithe pins in the schematic.
- In the layout editor, will still see the net ratnest. Will want to use net labels attached directly onto pins that wish to connect rather than using graphical wires electrically.
- Net labels make it easier to manage the physical characteristics of traces based on their net membership and use of the net classes.
## Schematic Editor
![[Pasted image 20260417151115.png]]

![[Pasted image 20260417151914.png]]
- Can configure the thickness, color and style of a wire or bus ()based on the net class membership of the wire or bus. Can also create new net classes or edit and delete existing classes.
- Busy schematics with many net and net classes, can use the Filter Nets group of widget to narrow down the nets listed in the membership pane.
- Assign Net Class pane, can set a net class for the nets have selected in the membership pane.
## Assign a net to a net class
![[Pasted image 20260417151942.png]]

- Click on the net row on the membership pane to select it.
- Select the target net class from the drop-down menu in the Assign Net Class pane and click "Assign To Selected Nets".
	- Click on the "+" button of the Net Class list pane to add a new net class and the fi eld in each row to make changes