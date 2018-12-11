# Altium Designer Notes and PCB Design Guidelines
How to design a standard PCB layout using Altium Designer
<br />**This document is currently in a work in progress.**

<p align="center"> 
<img src="https://www.altium.com/altium-designer-coming-soon/theme/images/AD_FirstScreen_X2_black.png">
</p>

## Table of Contents
- General Information
- [Shortcut Keys](#shortcut-keys)
- Components
- [Schematics](#schematics)
- [Setup Before Layout](#setup-before-layout)
  - [Rules](#rules)
  - [Stackup](#stackup)
  - [Set Net Colors](#set-net-colors)
- [Placement](#placement)
- Layout
- High Speed Tips
- [Useful Links](#useful-links)

## Shortcut Keys

All Altium Designer Shortcut Keys [[Download](http://valhalla.altium.com/Learning-Guides/Legacy/GU0104%20Shortcut%20Keys.PDF)]
<br />+400 Shortcuts for Altium Designer [[View](https://shortcutworld.com/Altium-Designer/win/Altium-Designer_Shortcuts)]

### Schematic Designer
- **General**
   - `Ctrl` + `M`: Measure.
   - `C` Then `C`: Compile the active project.
   - `D` Then `U`: Update the PCB with any schematic changes.
   - `D` Then `O`: Open the “Document Options” window.
   - `Q`: Toggle the measurement unit system between metric and imperial.
   - `T` Then `C`: Cross-probe a net, pin or component between the schematic and the PCB.
- **Schematic Routing**
   - `P` Then `W`: Start placing wires.
- **Component Placement**
   - `J` Then `C`: Jump to component.
   - `J` Then `N`: Jump to net.
   - `T` Then `A` Then `A`: Open the “Annotate” window.
   - `T` Then `A` Then `U` Open the “Quick Annotate” window.
### PCB Designer
- **General**
   - `D` Then `I`: Import changes from schematic to PCB.
   - `T` Then `D` Then `R`: Run DRC (Design Rule Checks).
   - `Q`: Toggle the measurement unit system between metric and imperial.
   - `T` Then `C`: Cross-probe a net, pin or component between the schematic and the PCB.
- **Routing**
   - `P` Then `T`: Begin routing a track. 
   - `Tab` (while routing): Brings up routing options/properties windows.
   - `Shift` + `Space`: Change the track routing style (e.g. from straight to 45 to curved and back again).
   - `Shift` + `W`: Set the track width to something from the predefined track width list.
   - `T` Then `G` Then `A`: Repour all polygons.
- **Component Placement**
   - `L`: Flip a component.
   - `Spacebar`: Rotate object by 90°.
   - `J` Then `C`: Jump to component.
   - `Ctrl` + `Shift` + `C`: Align horizontal centers.
   - `Ctrl` + `Shift` + `T`: Align horizontal tops.
   - `Ctrl` + `Shift` + `B`: Align horizontal bottoms.
   - `Ctrl` + `Shift` + `V`: Align vertical centers.
   - `Ctrl` + `Shift` + `L`: Align vertical lefts.
   - `Ctrl` + `Shift` + `R`: Align vertical rights.
   - `E` Then `M` Then `M`: Move component (useful for when you can’t select it because it’s ontop of other components).
- **Visualisation**
   - `Shift` + `S`: Hide all but selected layer.
   - `V` Then `B`: Flip board.
   - `MouseScroll`: Move up/down.
   - `Shift` + `MouseScroll`: Move left/right.
   - `Ctrl` + `MouseScroll`: Zoom in/out.
   - `Ctrl` + `M`: Measure.
   - `+` / `-`: Increment/Decrement through the enabled layers.
   - `*`: Increment/Decrement through routing layers only.
   - `S` Then `S` / `Ctrl` + `H`: Enables you to select a section of connected copper. Stops the selection at a via, pad or intersection.
   - `D` Then `T` Then `<letter>`: Select a view configuration. These views and their key shortcuts are user configurable.
     - `D` Then `T` Then `U`: Selects the “up” configuration (all top layers).
     - `D` Then `T` Then `D`: Selects the “down” configuration (all bottom layers).
   - `D` Then `O`: Open Board Options window.
   - `Ctrl` + `G`: Open the Grid Editor window.
   - `L`: Show the Layers dialog box to adjust the visible layers and/or enable/disable layers.
   - `G`: Cycle through the predefined grids.

## Schematics

- Draw circuits from **left to right** and **top to bottom**.
- Draw circuits in functional block and use **Net Labels** for connecting blocks to each other.
- Use **standard designators**:
   - IC: IC or U
   - Resistor: R
   - Capacitor: C
   - Inductor: L
   - Transistor: Q or T
   - Diode/LED: D
   - Crystal: Y/XTAL
   - Pin headers: J
   - Jumper: JP
   - Fuse: F
   - Ferrite Bead: FB
   - Fiducial: FD
   - Test point: TP
- Add the **Cover Page** to the schematic:
   - Project name
   - Date
   - Re/version number
   - All the names of schematics
   - Notes legend
   - Company information
   - Schematic status with date (Draft, Preliminary, Checked, Released)
      - Draft: Blocks, just the structure of the schematic.
      - Preliminary: Connections done, Quiet close to final.
      - Checked: No mistakes in schematic.
      - Released: PCB sent for fab.
- Don't connect 4 wires at one junction.
- Place all labels, designators, pins, text etc. **horizontally**.
- **Don't fill up** the whole sheet.
- Name schematics with **clear** and **short** name.
    - For example: Use CPU_HDMI and CPU_LVDS instead of CPU1 and CPU2.
- Use "**+...V...**" for power nets
    - **Never use "VCC" as net name!**
    - For example: +12V, +5V, +3V3, +2V5, and etc.  
- **Fill information** in Title block.
- Use **distinctly** and **clear** names for schematics.
- Add useful **Design Notes** on the schematic.
- If you suspect that there are parts in the circuit, place them. If you do not need them, you can remove them later!
- **Double check** RX & TX pins.
    - **Never use "TX" & "RX" as net name alone!**
    - For example: Use MCU_TX or GPS_RX instead of TX or RX alone!
- Put enough and useful Test Points (TPs) for circuit debugging.
- Place components in the schematic **close to the pins** where they should be located on PCB.
    - For example: bypass capacitors.
- Generate **PDF** of the completed schematic.

## Setup Before Layout

### Rules
- **Clearance**
   - `D` Then `R` > `Design Rules` > `Electrical` > `Clearance`
   - Clearance = 0.2 mm  
- **Routing**
   - `D` Then `R` > `Design Rules` > `Routing` > `Width`
   - Min Width = 0.254 mm
   - Preferred Width = 0.3 mm
   - Max Width = 0.5 mm
   - `D` Then `R` > `Design Rules` > `Routing` > `Width_PWR`
   - Min Width (PWR) = 0.254 mm
   - Preferred Width (PWR) = 1 mm
   - Max Width (PWR) = 4 mm
   - `D` Then `R` > `Design Rules` > `Routing` > `Routing Via Style`
   - Via Diameter = 0.6 mm
   - Via Hole Size = 0.3 mm
- **Mask**
   - `D` Then `R` > `Design Rules` > `Mask` > `Solder Mask Expansion`
   - Solder Mask Expansion = 0.1 mm
- **Manufacturing**
   - `D` Then `R` > `Design Rules` > `Manufacturing` > `Hole To Hole Clearance`
   - Hole to Hole Clearance = 0.3 mm
   - `D` Then `R` > `Design Rules` > `Manufacturing` > `Minimum Solder Mask Silver`
   - Minimum Solder Mask Silver = 0.3 mm
   - `D` Then `R` > `Design Rules` > `Manufacturing` > `Silk to Solder Mask Clearance`
   - Silk to Solder Mask Clearance = 0.1 mm
   - `D` Then `R` > `Design Rules` > `Manufacturing` > `Silk to Silk Clearance`
   - Silk to Silk Clearance = 0.1 mm
- **Placement**
   - `D` Then `R` > `Design Rules` > `Placement` > `Component Clearance`
   - Component Clearance (Vertical) = 0.2 mm
   - Component Clearance (Horizontal) = 0.2 mm
- **Via** 
  - `DXP` > `Prefs` > `PCB Editor` > `Defaults` > `Via`
  - Via Diameter = 0.6 mm
  - Via Hole Size = 0.3 mm

### Stackup
- `Design` > `Layer Stack Manager`
- Change Layer Names to L1 and L2, and etc.
- Thickness of Dielectric (PCB Thickness) = 1.6 mm

### Set Net Colors
- `View` > `Panels` > `PCB`
- `PCB Panel` > `<Net Name>` > `Right-Click` > `Change Net Color`
- `PCB Panel` > `<Net Name>` > `Right-Click` > `Display Override > Selected ON`
- Net Color for GND = Blue (236)
- Net Color for PWR = Orange (4) or Pink (1)
- `F5` = Toggle Net Colors

## Placement

- Plan layout first, then placement.
- Start with **BMC (Big, Main and Critical)** components. e.g. MCU and clock devices.
- Place **predefined location** of components and connectors.
- Isolate **analog and digital** power supply sections.
- Place **clock driver** close to clock oscillator.
- **Arrange** components in rows and columns.
- Arrange components with **uniform orientation**, e.g. diodes and polarized capacitors.
- **Indicate polarity** on silk screen.
- Place all components on **top side** of the PCB. On complex and compact designs place **short height** and/or **low thermal dissipation** components go on bottom, never place tall components on the bottom side else it will increase the total height of the PCB.
- Keep 1mm (40mil) **space** between components and 2.5 and/or 3 (100mill and/or 120mil) from component to edge
- Place **bypass capacitors** as close to IC as possible, use combination of 10uF and 100nF, place smaller cap closer to IC.
- Place **connectors** on one edge of the board.
- Place at least four **mounting holes**.
- Make sure **enough space** around mounting holes for screw heads to sit on and try placing big components around PCB.
- Keep more space around **headers/connectors**.
- Place **hot components** on the top side of the PCB.
- Must place **test points** on all power nets and optional critical signals and programming pins if needed.

## Useful Links
- [Open Source Altium libraries](https://github.com/amiryeg/Altium-Libraries)
- [3D and 2D CAD Models](https://www.3dcontentcentral.com/)
- [PCB Trace Max Current Calculators](https://www.eeweb.com/tools/external-pcb-trace-max-current)
- [Trace Width Calculators](https://www.eeweb.com/tools/external-pcb-trace-width)
- [PCB Trace Resistance Calculator](https://www.eeweb.com/tools/trace-resistance)
- [Impedance Calculators](https://www.eeweb.com/tools/microstrip-impedance)







