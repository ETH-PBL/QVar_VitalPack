# Schematic review checklist
## Style
- [x] Does each schematic sheet have the correct template applied?
- [ ] Is the title block filled out on each sheet?
- [x] Can the sheet sizes be printed on your office’s printer?
    -  Sheets should not exceed Tabloid/A3 size.
- [x] Are all schematic sheets the same size?
- [x] Do nets have netlabels to ease readability and PCB layout?
- [x] Are nets consistently labeled?
- [x] Are power ports consistently labeled?
- [x] If there are multiple sheets:
    - [x] Is there a top sheet?
    - [x] Does the top sheet show connections between each sub-sheet?
    - [ ] Do you need a table of contents? - *not needed, small design*
- [x] Does the schematic design compile and pass design rules without errors?
- [x] Has each warning from compiling the schematic design been checked to see if it is actually critical?
- [ ] ~~Is there a change list or revision list if this is not the first design review for the schematic?~~
- [x] Are all components aligned to the grid, and are all the net wires correctly connected to each pin?
- [x] Can groups of offsheet connections be grouped into a bus, or harness to improve the legibility of the top sheet?
- [x] Are multi-channel blocks implemented as multi-channel sheets?
- [ ] ~~Are differential pairs correctly identified with _P and _N signals?~~
- [ ] ~~Do differential pairs have a differential pair label?~~
- [ ] ~~Are there net classes applied to each net that needs it?~~
    - [ ] High voltage
    - [ ] High current
    - [ ] RF/Impedance matched
    - [ ] Differential pairs
- [x] Do all components have the correct designators? (i.e.: You annotated the schematic)
## Usability/Testing
- [ ] Is there a LED for each power rail? At least for the input?
    *No, low power design*
- [x] Are there test points for each power rail?
- [x] Are there test points for critical signals/signals of interest?
## Production
- [x] Can any component values be safely merged to reduce BOM line items?
- [ ] Is only one part number specified for each passive component value with a specific size?
- [ ] Check that each symbol has a manufacturer and part number assigned.
- [ ] Are all components active production, and not end-of-life/discontinued/not recommended for new designs at the time of the schematic review?
- [ ] Does each component have sufficient stock in the supply chain?
## Connectors
- [x] Check that I/O pins have a pull-up or down to define their default state when disconnected.
- [x] Ensure there is a decoupling capacitor for each power pin on the connector.
- [ ] ~~Do electrically noisy pins need to be treated as pseudo-differential pairs?~~
- [ ] ~~Do long cables need to be isolated for EMC?~~
## Components
- [ ] Check all symbol pinouts against the datasheet, even if you have used the IC before or trust the symbol source.
- [ ] Tantalum Capacitors' voltage rating is at least 20% higher than the maximum expected voltage.
- [ ] ~~Have you checked the current passing through each resistor for power dissipation?~~
    - [ ] ~~Is it safely within the rating of the components?~~
    - [ ] ~~Will the temperature of the resistor be too high, even if it’s within the ratings?~~
- [ ] ~~Is each resistor’s voltage rating sufficient for the maximum voltage applied (mostly relevant to 0402 and smaller sizes)?~~
- [ ] ~~Have all the current limiting resistors been correctly calculated for each LED's forward voltage?~~
- [ ] ~~Have all the current limiting resistors been correctly calculated for each optoisolator forward voltage?~~
- [ ] Do reset/enable pins need an external pull-up or pull-down resistors?
- [ ] ~~Are any potentially floating pins pulled up or down with external resistors?~~
    - [ ] ~~Pins drove with diodes~~
    - [ ] ~~Pins drove with transistors or MOSFETs~~
    - [ ] ~~Comparator outputs~~
- [ ] ~~Are any pins with a state that is critical at power up externally pulled up or down?~~
    - [ ] ~~Gate/base pins on MOSFETs and transistors~~
    - [ ]~~ External connectors~~
    - [ ] ~~Safety devices~~
    - [ ] ~~Thermal management devices~~
- [ ] ~~Do any programmable devices have a programming header/pad accessible?~~
*External board has to be used for programming. testpoints are supplied for emergency situations*
    - [ ] ~~For prototypes, can you read/write flash/EEPROMs externally with a connector?~~
- [ ] Check for the correct polarity of each diode or LED.
## Power
- [x] Every power pin of every IC should have a decoupling capacitor.
- [x] Do multiple voltage rails need sequencing?
    *has to be implemented in software*
    - [ ] Is it implemented?
- [ ] Does each voltage regulator’s output meet the precision requirements for the subsystems connected to it?

- [ ] Is there a linear regulator between any devices that need extremely clean power (e.g.: operational amplifiers with high gain) and a switched mode regulator source?
## Signal
- [ ] ~~*Are there filters on every Analog to Digital converter pin?*~~
- [ ] ~~Have amplifier circuits been simulated to ensure they are stable?~~
- [ ] ~~Have all voltage dividers been re-calculated to ensure the output voltage is correct?~~
- [ ] ~~Is there capacitance and/or a Zener diode on the output of each operational amplifier?~~
- [ ] Are all signals feeding into logic devices within the maximum voltage rating?
## EMI/EMC/Protection
- [ ] Does every externally accessible connection/exposed piece of metal have adequate ESD protection? Keep in mind that ESD spark gaps for what is exposed.
    - [x] Connector pins
    - [ ] Connector housings
- [ ] ~~Does the input power require a fuse to protect upstream devices?~~
- [ ] Is the input power protected against reverse polarity?
*Internal protection in vitalcore*
- [ ] Is there overvoltage protection on the power input?
*No, care has to be taken to prevent magic smoke*
- [ ] Is there overcurrent protection on the power input?
*see above*
- [ ] Are there current limiting resistors on nets from external devices to sensitive devices (e.g.: microcontroller pins)
- [x] Is there input under-voltage protection?
- [x] Is there short circuit protection on each voltage rail that has an external connection/output?
- [ ] Does every switching regulator have a sufficient input filter to prevent conducted EMI from escaping on its input?

