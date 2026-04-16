# Schematic symbols
![[Pasted image 20260414154733.png]]
- Large rectangular symbol with the designator 'ZU4' is the ATMEGA328P-PU microcontroller chip. Contains several pins that provide input and outputs and each of them is named.
- Few capacitors, designated C5, C10 and C6, none of them polarized. There is 1 resistor, R2 and few resistor network (RN2 and RN1).
- There are also symbols for an LED, jumper connector and power (Vcc , RAW and GND).
# Difference style
American style symbols will have the postfix 'US' in their name.
![[Pasted image 20260414174910.png]]

# PCB Key Terms
## FR4 (Flame Retardant)^[A desireable quality for a board that will hold together component that can potentially ignite when they fail]
- Used to make printed circuit boards. 
- It is a glassed-reinforced epoxy laminate composite material.
**Characteristic**
- Very light and strong
- Does not absorb water
- Excellence isolator
- Maintains its quality in dry and humid environments
G-11 for application that must operate in high temperature.
## Traces  (tracks) 
![[Pasted image 20260414175824.png]]
- Electrical signals and power use traces to travel throughout a circuit.
- Have total control over the characteristics of traces. Can control with their width, height and route, including the angles by which a tree changes direction.
- Trace to accommodate a large current flowing through it with little resistance and temperature rise, can design it wider and thicker.
- Keeping the width of traces to around 0.3mm makes it possible to draw traces closer together and reduce the final size of PCB.
![[Pasted image 20260415104705.png]]
- Much wider traces than regular signal traces. These traces connect the terminals of a 240 Volt relay.
### Holes
### TH (through-hole)
  - Through-hole components are easier work with.
  - Hobbyist common use.
### SMD Pads(surface-mounted device)
  - Components are smaller. 
  - Tend to not to use them until they are more comfortable with with their soldering skills. 
  - Easy to work with as their TH counterparts.
  - Can be populated automatically using pick and place machines and because their small size results in smaller PCBs.
![[Pasted image 20260415110316.png]]

![[Pasted image 20260415104848.png]]
- Connect the front for the PCB with the back electrically. Can see that the gold plating of the pad fills the inside of the hole.
![[Pasted image 20260415110513.png]]
**Plated-Through Hole (PTH)**
- More common variety and default type of hole in more cases.
- Use a drill to create the hole and then copper to cover the hole's sides that its 2 ends.
- Vias except they have a smaller diameter, it is impossible to accommodate component pins.

**Non-Plated Hole (NPTH)**
- Use the same drill to create the hole,  traces inot copper is used to cover the sides of the hole, there is no electrical connection between its 2 ends.
- Pads without holes are useful for attaching surface-mounted components.
# Via
- Want to move a signal that travels across a trace from 1 side of PCB to another.
- Via hole with sides covered with copper or gold that allows a trace to continue its route across layers.
- Vias are similar to through-hole pad except the don't have any exposed copper and pad.
![[Pasted image 20260415111458.png]]
Left: The arrows point to 2 vias in the front of the PCB.
Right: The circles indicate the same vias on the back of the PCB.
# Layer of PCB
**It is possible to create all traces on 1 layer of PCB.**
- PCB gets busy with more components, it quickly become impossible to do the routing on a single layer.
- When multiple layers are needed, vias provide the simplest method of allowing a trace to use the available board real estate.
![[Pasted image 20260415112945.png]]
- Buried via
  That connects any 2 internal layers. In1.Cu and In2.Cu.
- Blind via
  connects 2layers but has 1 end exposed to the outside of the board, either top or bottom.
- Micro via
  made using a high-powered laser instead of a mechanic drill, the use of lasers makes it possible to reduce the diameter of the via dramatically.
# Annular ring
- The area on a pad that surrounds a via.
![[Pasted image 20260415113746.png]]
- Primary metric of an annular ring is its width, defined as the minimum distance between the edge of the pad and the edge of the via or pad hole.
- Width of 2 annular rings is marked with 2 red lines.
- The drill hit is in the middle of the pad. If the drill bit is not aligned correctly, the hole can be closer to 1 to 1 edge of the pad^[tangency] or could even miss the pad completely^[breakout].
# Soldermask
**Why we need?**
- Copper slowly reacts with oxygen in the air, resulting in oxidization.
- Oxidized copper produces a pale green outer layer. With a solder mask, a thin layer of polymer that insulates it from oxygen. It also prevents solder bridges from forming between pads.
![[Pasted image 20260415114618.png]]
- The copper is protected by a thin layer of green solder mask. Only the pads and the mounting holes are not covered by the solder mask.
# Silkscreen
- To convey useful information and add a touch of elegant. Rasperry Pi logo, logos of various certification and different text items.
# Drill bit
****![[Pasted image 20260415115146.png]]****
- Used to create holes, vias and cutouts.
- The drill are attached to computer-controlled drilling machines and guided by a file that contains information about the coordinates and drill size for each hole.
- These vias that connect in-between layers of the PCB.

Typically made of solid coated tungsten carbide material and size:
- 0.3 mm
- 0.6 mm
- 1.2 mm
# Drill hit
- Describe the location on the PCB where the drill bit comes it contact with the PPCB and creates a hole.

![[Pasted image 20260415115500.png]]
- A highly integrated microprocessor, memory communications and connectors. Even the connectors are SMD.
- Would result in a board that was man times the size of the Rasberry Pi Zero and would cost many times more because most of the assembly would have to be done by hand.
# Gold Finger
- Gold-plated connectors placed on the edge of a PCB.
- Useful for interconnecting 1 board to another.
- Gold fingers to connect to other devices via a slot, motor controllers and sensors.
- Make it possible to attach and detach the PCB to slot at least 1 000 times before they start to wear out.
![[Pasted image 20260415120040.png]]
# Keep out areas
- An area on the PCB that must be clear of components and even trace.
- Can also configurate the keep-out area to prevent the user from adding specific or all types of elements.
**3 examples of devices that contain keep out areas.**
![[Pasted image 20260415120452.png]]
- They contains an integrated antenna that requires a patch of PCB clear of components and other traces.
- The front side is where the TFT screen is placed. Can see that the screen's ribbon connector is attached to a row of pads in the back of the PCB. We can mark a keep-out area in the front of the PCB only and allow for footprints and traces to be placed on the back of the PCB.
- There is no risk placing a footprint by mistake and obstructing the travel path of the notch.
# Panel
- Each panel can contain many copies of the same PCB. It is also possible to use clever algorithms that place different PCBs on the same panel that the panel's capacity is fully utilized and that the individual cost of each PCB is reduced.
- A single panel contains 4 individual PCB. 4 PCBs are populated while still part of the panel using automated pick and place machine.
- That uses an arm to pick each component from container and places it precisely on the pads.
![[Pasted image 20260415121442.png]]
![[Pasted image 20260415121502.png]]
# Solder paste
![[Pasted image 20260415121859.png]]****
![[Pasted image 20260415122324.png]]
- A soft and sticky material applied on pads.
- To help attach an SMD component to the pad. With solder, will need a soldering iron to heat it, melt it and apply it on a component pin already in place.
- Will first use a syringe to cover the pad, then place the component on the ad and provide heat it the form of an oven to heat the paste and bond with the pad and the component's plated area.
- Syringe paste in a syringe dispenser that can purchase from retailers. The syringe equipped with a thin nozzle, can manually deposit a small amount of solder paste on the pads.
- Using tweezer, can place the component want to attach on the solder paste. After have all the components want on the board, place the board in an oven to bake it. After baking process is complete, the solder paste becomes solid.
# Stencil
![[Pasted image 20260415122530.png]]
- Cut to have openings of the exact size and the precise location of the board's pads. The technician will place the stencil over the board and then apply the paste remains on the pads only.
- The components are placed on the pads and stick  on them because of the paste.
- Reflow oven is an industrial sized machine used to complete  attaching SMD components on a PCB.
# Pick and place
- That assemble the various components on the surface of a circuit board.
![[Pasted image 20260415122812.png]]
**Includes:**
- A repository of the various components that are to be placed on the board.
- A conveyor belt that brings in the boards.
- An inspection system composed of cameras that can optically recognize the board, components and other guidance markings on the boards.
- A robotic arm that can pick a component from the repository and place it on the board.