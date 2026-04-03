gitlab: https://gitlab.com/kicad/code/kicad.git
version: 10.0

| extension | function                      |
| --------- | ----------------------------- |
| kicad_pro | contains project information  |
| kicad_pcb | contains layout information   |
| kicad_sch | contain schematic information |
# Schema
![[Pasted image 20260311105657.png]]
- Can span over multiple sheets. If schematic is too large to fit in 1 sheet comfortably.
- Capture all necessary information that the layout editor uses:
	- Component
	- Wires that connect pins net
	- Various kinds of netlabels, busses, power nets.
# 2 kicad_sch
- It is the schematic file created by Eeschema.
## Eeschema
- The tool used to draw the circuit diagram. Used to create the logical circuit diagram.
![[Pasted image 20260311103900.png]]
### What are the thing can do?
- Place electronic symbols
- Connect wires
- Add labels
- Assign footprints to components.
- Run Electrical Rule Check (ERC)
Trace have names
![[Pasted image 20260311110933.png]] 
## Pcbnew
- Is used after the schematic is finished. Design the physical PCB
- Route copper tracks
- Design board shape
- Add vias
- Prepare files for manufacturing.

![[Pasted image 20260312092404.png]]
- Layout editor allows you to select the layers and design elements want to see.
- Can enable or disable the visibility of layers, footprints, tracks, zones and vias.
![[Pasted image 20260312092609.png]]