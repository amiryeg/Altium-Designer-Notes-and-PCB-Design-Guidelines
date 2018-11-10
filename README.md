
# Altium Designer Notes and PCB Design Guidelines
How to design a standard PCB layout using Altium Designer
<br />**This document is currently in a work in progress.**

<p align="center"> 
<img src="https://www.altium.com/altium-designer-coming-soon/theme/images/AD_FirstScreen_X2_black.png">
</p>

## Table of Contents
- [Setup Before Routing](#setup-before-routing)
   - [Rules](#rules)
   - [Stackup](#stackup)
   - [Set Net Colors](#set-net-colors)
 
## Setup Before Routing

### Rules
- **Clearance**
   - `D + R > Design Rules > Electrical > Clearance`
   - Clearance = 0.2 mm  
- **Routing**
   - `D + R > Design Rules > Routing > Width`
   - Min Width = 0.3 mm
   - Preferred Width = 0.3 mm
   - Max Width = 0.5 mm
   - `D + R > Design Rules > Routing > Width_PWR`
   - Min Width (PWR) = 0.4 mm
   - Preferred Width (PWR) = 0.4 mm
   - Max Width (PWR) = 4 mm
   - `D + R > Design Rules > Routing > Routing Via Style`
   - Via Diameter = 0.6 mm
   - Via Hole Size = 0.3 mm
- **Mask**
   - `D + R > Design Rules > Mask > Solder Mask Expansion`
   - Solder Mask Expansion = 0.1 mm
- **Manufacturing**
   - `D + R > Design Rules > Manufacturing > Hole To Hole Clearance`
   - Hole to Hole Clearance = 0.3 mm
   - `D + R > Design Rules > Manufacturing > Minimum Solder Mask Silver`
   - Minimum Solder Mask Silver = 0.3 mm
   - `D + R > Design Rules > Manufacturing > Silk to Solder Mask Clearance`
   - Silk to Solder Mask Clearance = 0.1 mm
   - `D + R > Design Rules > Manufacturing > Silk to Silk Clearance`
   - Silk to Silk Clearance = 0.1 mm
- **Placement**
   - `D + R > Design Rules > Placement > Component Clearance`
   - Component Clearance (Vertical) = 0.2 mm
   - Component Clearance (Horizontal) = 0.2 mm
- **Via** 
  - `DXP > Prefs > PCB Editor > Defaults > Via`
  - Via Diameter = 0.6 mm
  - Via Hole Size = 0.3 mm

### Stackup
- `Design > Layer Stack Manager`
- Change Layer Names to L1 and L2, and etc.
- Thickness of Dielectric (PCB Thickness) = 1.6 mm

### Set Net Colors
- `View > Panels > PCB`
- `PCB Panel > "Net Name" > Right-Click > Change Net Color`
- `PCB Panel > "Net Name" > Right-Click > Display Override > Selected ON`
- Net Color for GND = Blue (236)
- Net Color for +5V = Orange (4)
- Net Color for +3V3 = Pink (1)
- `F5` = Toggle Net Colors


