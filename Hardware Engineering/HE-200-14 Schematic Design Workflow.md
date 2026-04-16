![[Pasted image 20260408111059.png]]
- Engineering and design is a massively iterative process. Linear simply doesn't work.
# Step 1: Setup
- Configure the grid size
- Set up the page.
![[Pasted image 20260415123518.png]]
![[Pasted image 20260415123544.png]]
- Set the grid thickness, minimum spacing and snap to grid. The snap feature helps in the drawing process that lines, pins and other elements align well.
![[Pasted image 20260415123804.png]]
- When print out schematic, this information will also be included.
# Step 2: Symbols
![[Pasted image 20260415123917.png]]
- Involves getting all the needed symbols from the symbol chooser and adding them to the schematic sheet.
![[Pasted image 20260415124050.png]]
# Step 3: AAA (Arrange, Annotate, Associate)
- Move the symbols in place and prepare them for wiring.
- To keep the wires short and prefer straight lines whenever possible to produce amore readable schematic.
![[Pasted image 20260415124340.png]]
- Before moving to the wiring step, should also annotate the symbol. 
- The question marks indicate that these symbols have not been annotated.
![[Pasted image 20260415124511.png]]

![[Pasted image 20260415124620.png]]
In the association table, the symbols appear in the left column and their assigned footprints in the left.
# Step 4: Wire
![[Pasted image 20260415124934.png]]
- Connect the symbols using wire. Each wire is attached to a symbol pin and creates a net.
- The green wires connect the LED and the resistor to the 5V voltage source and the GND.
- This schematic contain 3 wires, so it includes 3 nets.
- The examples here don't have a custom net name, but they have an automatically assigned name that Eeschema has generated. With or without a custom net name, this schematic is fully weird.
# Step 5 : Nets
- Power nets are implemented with wider traces to allow them to accommodate higher currents.
- The geometry of those nets, once implemented as traces is essential and having a custom name make their manipulation easier.
![[Pasted image 20260415125452.png]]
# Step 6: Electrical Rules Check (ERC)
- The equivalent is to periodically run the compiler every time complete a new code segment. 
- The ERC will check for various error conditions such as unconnected pins, power pins, problems connecting to incompatible pins.
![[Pasted image 20260415140708.png]]
# Step 7: Comments and Graphics
- Comments come in text labels that highlight schematic features and graphics such as lines and boxes that help group segments of the schematic into 