# QVAR 6-Channel VitalCore Backpack

## A high-precision 6-channel physiological sensing interface board for VitalCore

Federico Villani, ETH Zurich PBL, IIS, 2023

- Board documentation: [QVAR VitalCore Backpack](hardware/Documentation/QVAR_VC_FULL_DOC.PDF)

## Overview

The QVAR 6-Channel VitalCore Backpack (QVar VitalPack) features six QVar channels, providing a flexible system for testing and implementing various combinations of electrode positions. Its compact size 19.5 mm×16.5 mm and light weight (1.12 g) make it ideal for integration into wearable devices.

### Key Features

- **6 Independent differential or single-ended Channels**: Can use either ST1VAFE3BX or LIS2DUXS12. Depending on the configuration, the channels can be used for differential or single-ended measurements.
- **VitalCore Interface**: Native compatibility with [VitalCore v1.3](https://github.com/ETH-PBL/VitalCore)
- **Compact Form Factor**: Space-efficient (19.5 mm×16.5 mm) design for portable and wearable applications
- **Signal Conditioning**: Integrated filtering and ESD protection
- **Power Management**: Possibility to use either DC-DC converters on VitalCore or LDOs.

## System Architecture

### Core Components

- **6x QVAR Channels**: The 6 QVAR channels (QA1, QA2, QB1, QB2, QC1, QC2) are attached to 3 different I2C buses (I2CA, I2CB, I2CC) with 2 channels per bus. The I2C interface can be changed to SPI with a minor modification of the PCB.
- **Power Management**: The QVAR channels can be powered either by VitalCore VCORE voltage rails or by VA0 rail (VitalCore LDO) and VD2 rail (VitalCore DC-DC converter) output (by changing position of jumpers JP_A and JP_D). The QVAR channels attached to I2CB bus have to be powered by VCORE as the I2CB bus is always on on VitalCore.
- **Analog connections**: Differential measurement channels can be attached to the 1.27mm pitch connectors on signal Q1 and Q2 (Q1 and Q2 are the differential inputs for Plus and Minus electrodes of the QVAR chip). Single-ended channels can be attached either to Q1 or to the UMC connectors on the back-side of the PCB. 
- **Operating Voltage**: Nominal 1.8V, Compatible with VitalCore power rails



## Repository Structure

```text
6QChan_vitalcore_backpack/
├── PCB/                           # PCB design files
│   ├── main.SchDoc               # Main schematic
│   ├── Interface.SchDoc          # Interface circuitry
│   ├── QVAR.SchDoc              # Channel schematic
│   ├── QVAR6_VC_Backpack.PcbDoc # PCB layout
│   └── Libraries/               # Component libraries
├── Documentation/               # Project documentation
│   ├── QVAR_VC_assembly.PDF    # Assembly documentation
│   ├── QVAR_VC_schematics.PDF  # Schematic documentation
│   ├── QVAR_VC_FULL_DOC.PDF    # Complete design documentation
│   ├── BOM/                     # Bill of materials
│   └── Manufacturing/          # Manufacturing files
│       ├── Gerber/             # Gerber files for fabrication
│       └── NC Drill/           # Drill files
├── Draftsman/                  # Assembly and manufacturing drawings
├── settings/                   # Project configuration
└── 6QChan_vitalcore_backpack.PrjPcb  # Altium Designer project
```

## Technical Specifications


### PCB Specifications

- **Layer Count**: 6-layer
- **PCB Thickness**: 0.8mm 
- **Via Technology**: through-hole vias, filled and plated (Via in pad)
- **Surface Finish**: ENIG

## Getting Started

### Prerequisites

- Altium Designer (recommended version 20.0 or later)

### Viewing the Design Files

1. **Open the project**:

   ```bash
   Open 6QChan_vitalcore_backpack.PrjPcb in Altium Designer
   ```

2. **Navigate the design**:
   - `main.SchDoc`: System-level connections and interfaces
   - `Interface.SchDoc`: VitalCore interface circuitry
   - `QVAR.SchDoc`: Individual channel design (hierarchical)
   - `QVAR6_VC_Backpack.PcbDoc`: Complete PCB layout

3. **Generate documentation**:
   - Use the OutJob file in `settings/QVAR_VC_Backpack.OutJob`
   - Generate PDFs, Gerber files, and BOMs as needed

## Manufacturing and Assembly

### PCB Fabrication

Complete manufacturing data is provided in the `hardware/Documentation/Manufacturing/` folder:

- **Gerber Files**: Complete layer stackup and routing
- **Drill Files**: Via and mounting hole specifications

## Documentation

- **Schematics**: Complete electrical schematics (`QVAR_VC_schematics.PDF`)
- **Assembly Guide**: Assembly instructions and component placement (`QVAR_VC_assembly.PDF`)
- **Complete Documentation**: Full design package (`QVAR_VC_FULL_DOC.PDF`)
- **Manufacturing Files**: Fabrication and assembly data packages

Access all documentation in the `Documentation/` folder.

## Usage


### Channel Configuration

- Each QVAR channel can be independently configured
- Proper grounding and shielding essential for biomedical applications
- Reference electrode connections for differential measurements



## Publications

If you use the QVAR 6-Channel VitalCore Backpack in an academic or industrial context, please cite the relevant publications:

```bibtex
TODO ADD PUBLICATION
```

## Contributing

This is an open hardware project. Contributions are welcome in the form of:

- **Design Improvements**: Enhanced performance and optimization
- **Documentation Enhancements**: Better assembly guides and specifications
- **Bug Reports**: Issue identification and resolution

## License

This project is released under an open hardware license:

- **Hardware Design Files**: GNU General Public License v3.0
- **Documentation**: Creative Commons Attribution 4.0 International License (CC-BY-4.0)

## Contact and Support

For technical questions or collaboration inquiries:

- **Primary Contact**: Federico Villani ([villanif@ethz.ch](mailto:villanif@ethz.ch))
- **Organization**: PBL, IIS - ETH Zurich

## Version History

- **Version 1.0**: Initial release 
  
---

## Limitation of Liability

In no event and under no legal theory, whether in tort (including negligence), contract, or otherwise, unless required by applicable law (such as deliberate and grossly negligent acts) or agreed to in writing, shall any Contributor be liable to You for damages, including any direct, indirect, special, incidental, or consequential damages of any character arising as a result of this License or out of the use or inability to use the Work (including but not limited to damages for loss of goodwill, work stoppage, computer failure or malfunction, or any and all other commercial damages or losses), even if such Contributor has been advised of the possibility of such damages.
