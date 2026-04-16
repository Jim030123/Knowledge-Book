![[Pasted image 20260408111254.png]]
# Step 1: Setup
- Grid assists with the placement of footprints, drawing of traces and the drawing of the cutout of PCB. PCB provides multiple grid sizes, can also define custom size.
- Select grid size that is most appropriate for the design of the board's outline and placement of the footprints.
- Larger grid size for the board outline. Smaller one for the footprints.
**Example**
- Produce a rectangular PCB measures 50 mm x 30 mm.
  To place a few resistor, LED and headers. A reasonable grid choice for the outline and the larger features is 1.27 mm and 0.635 mm for the components.
  Traces 0.635 mm to 0.254 mm.

The larger grid will allow to draw the cutout of the board in precise 1.27mm segment. Will be able to draw the long side (50 mm) with  39 x 1.27 mm segment for a total length of 49.53 mm.

![[Pasted image 20260415142716.png]]


## Setting layer
- Create a single-layer PCB design, these manufacturers will use a 2 layer process.
 **Board Stackup**
![[Pasted image 20260415143247.png]]

- Project's technical requirements and  preferred manufacturer's capabilities and guidelines dictate the PCB design rules.
- It is good habit to confirm that, the design rules are compatible with the guidelines set by preferred manufacturer.
Minimum track width: 0.006
Minimum via diameter: 0.027
![[Pasted image 20260415144033.png]]

# Step 2: Outline and constraints
- Defines the shape of board. It is good practice to define the shape of board before add any component.
- Good practice to define the shape of board before add any components to it that can ensure that it will fit property within the confines of a project box or mechanical constraints.
- Defining the shape and the dimensions of PCB where must also define fixed features such as mounting holes and cuts.

## Edge.Cuts layer. 
- As mentioned in the Setup section, I prefer to use a large grid size while outlining.
- To create mounting holes and cutout, can choose one of a couple of methods. Make them in the Edge.Cuts layer or using pads during the component placement steps.
![[Pasted image 20260415145342.png]]

# Step 3: Place footprints
- Can proceed by placing the component.
- There is a requirement here to ensure sufficient space around the board for the cable.
- Have placed the connector facing in the opposite direction, the cable would interfere with work on the breadboard.
![[Pasted image 20260415145945.png]]
- The headers consists of the mean by which the power supply PCB plugs into the breadboard. The geometry of the breadboard severely restricts their positions.
## Principle to Follow
1. Components that are functionally related should stay close to each other.
2. Shorter traces are better.
3. Consider how the placement will affect assembly.
4. Consider component manufacturer specifications.
Thermal vias are vias that are not connected to a trace. They help move heat away from a component, such as an integrated circuit, through a die-attached paddle between the via and the component.

# Step 4a: Route
- Involves the drawing of the copper connections between the pads.
**To implement the traces between the pad:**
1. Start with any critical traces. This could include signal traces that have specific shape and length requirement like an onboard antenna.
2. Continue with power traces.
3. Finish with the rest the traces.
![[Pasted image 20260415150917.png]]
Micro:bit includes a trace Bluetooth antenna. Trace in the top left corner of the front the board. Because the antenna has strict geometrical specification for it to operate correctly.

## Power traces
- They convey a higher current than signal traces. It is appropriate it design power traces (GND, 5V, 3.3V).
- Should be around 0.30 mm to 0.40 mm in width for low voltage and low power consumption boards.
**Large Board**
- Can set up an autoroute that can save you some time.
**Smaller Board**
- Can finish routing manually.
## Step 4b: Copper fills
- Copper fill is an area on the board that is fully covered with copper.
- Create a ground plane, a contiguous mass of copper connected to electrical ground. Can create copper planes connected to a voltage level.
- PCB draws power from a battery, the ground plane is connected to the negative electrode of the battery and a voltage plane is connected to the positive electrode of the battery.
![[Pasted image 20260415152023.png]]
- Purpose if the thermals is to help with the soldering of the components on the pads.
- Pads were connected to the plane with a full pour of copper, the soldering iron's heat would dissipate into the copper fill too fast, and the pad would not be able to reach a temperature suitable for the solder melt.
- Reduce the heat dissipation speed, the thermals ensure electrical conductivity while managing the heat from the soldering iron.
### Benefits of using ground copper planes are:
1. They offer a degree of protection against electromagnetic interference.
2. They help to dissipate heat produced by the board components.
3. They enforce the discipline of placing signal traces on the top layer and connecting all ground pads to the bottom ground copper plan using vias.
A ground plane is created in the bottom of the PCB and often a V+ copper fill is created on the top layer. Suppose board uses multiple layers and multiple voltages.

Bottom layer: ground plane
Middle layer: positive voltages
Top layer: Signal

# Step 5: Silkscreen
- Artwork can be placed on the top and bottom layers.
**2 special layers dedicated to the silkscreens:**
- F.Sills
- B.Silks
The silkscreen artwork involves the following elements:
1. Descriptions of pad. This is done using text characters.
2. A name and version number of the board, also in text characters.
3. Logo and other graphics may want to include.
4. Other instructions that may assist the end-user include names, models and value of component, input and output voltage levels, email addresses or a website.
![[Pasted image 20260415154752.png]]
- It contains a prototyping board and has provision for a DHT22 sensor, a BMP280 sensor, a photoresistor and LED and it expose the I2C interface to connect an LCD screen. When fully assembled and tacked on Arduino Uno and an Ethernet Shield.
**Silkscreen**
- The name of the board and its version appear at the left edge of the board.
- BMP280 and DHT22 pads are marked. 
- Information on the values of the resistor and the cathode of the LED is marked.
- Prototyping area is marked. The rows of pins that convey GND and 5V levels are marked.
- The bottom of silkscreen where you can provide additional information. Bottom layer typically does not have components, there is more available real estate to use for this purpose.
![[Pasted image 20260415155057.png]]
# Step 6: Design Rules Check (DRC)
- Good habit to run the DRC frequently, at least very time you complete major trace routing or add a copper fill, should always run it when you are satisfied that the design work is complete and send the board to manufacturer.
![[Pasted image 20260415160105.png]]
- Get it to automatically refill zones before performing the DRC, to report all errors for tracks and do a couple of courtyard checks, courtyard overlap and footprints with missing overlaps.
- Footprint courtyard layers are F.CtrYd and B.CtrYd.
# Step 7: Export & Manufacture
- To turn the PCB from a set of files on computer into physical object.
- Must be careful to export the correct files with the correct file name extensions and units and not forget the drill files

![[Pasted image 20260415160934.png]]