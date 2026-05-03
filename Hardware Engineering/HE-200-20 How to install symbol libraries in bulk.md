![[Pasted image 20260417105307.png]]
- The repository contain footprints and symbols.
![[Pasted image 20260417105351.png]]
- Contains a collection of symbols (.lib extension) and their metadata (.dcm extension)
- Once the download is complete, expand the ZIP file and copy the resulting folder to preferred location.
- Can see the freshly downloaded Digikey folder in my project libraires folder.
![[Pasted image 20260417105825.png]]
- Bring up the symbol library manager. Will import the Digikey symbol collection into the Global Libraries list that all projects can use the new symbols files (.lib)
![[Pasted image 20260417110512.png]]
- Can double-click Digikey symbol to add to your schematic. That association is available in the footprint dropdown. It is unelectable. The footprint previewer is also empty. This is because haven't yet imported that footprints that come with Digikey collection. 
# How to create a custom symbol
![[Pasted image 20260417110910.png]]
Understand the process of creating a custom symbol, must first understand the element that make up a symbol, those element:
-  A rectangle or other closed shape that represents that the body of the symbol. Usually, the shape is filled with a color and has pins attached to its outline.
One or more pins:
- That attaches to the symbol outline and the side that connects to wires or labels.
- Type of a pin may be communicated with a symbol, such a large circle in the example of pin4. Each pin also has a number and a name.
- Typically the Vcc pin is placed on the top side of the symbol's rectangle, GND on the bottom and the functional pins on the left and right sides.
- A designator, the designator is "U".
https://techexplorations.com/guides/kicad/reference-designators/app_b/

- Name for the symbol. the name of the symbol appears in the "Value" field of its properties windows.
- The component's datasheet is the best source of information that is useful for creating custom symbols and footprints.
![[Pasted image 20260417112101.png]]

![[Pasted image 20260417112222.png]]
![[Pasted image 20260417112302.png]]
- With the symbol editor open, click on File and then "New Library" available to my current project.
- Select "Project" in the Add to Library Table and click OK.
- Symbol editor will ask to choose a location and click Save.
- Will see a new file with the ".kicad_sym".
- First select it before saving a new symbol in it, notice that text "no symbol" in the symbol editor's library filter.
![[Pasted image 20260417113207.png]]
![[Pasted image 20260417113335.png]]
- Make the new library available to my current project only, select "Project" in the "Add to Library Table".
- Used the suffix "\_PD" to denote symbols that I have created.
![[Pasted image 20260417115258.png]]

![[Pasted image 20260417120632.png]]
**Draw pins**
![[Pasted image 20260417121736.png]]

![[Pasted image 20260417121754.png]]

Choose a default footprint. To do this, click in the footprint field and the library button and use the footprint chooser to find a matching footprint such as the footprint chooser to find a matching such as the PDIP package.



