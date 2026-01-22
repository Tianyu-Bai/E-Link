PEDAL-256
An Open-Source, Solderless, High-Density Pedestal Connector for Neural Interfaces
<p align="center"> <img src="Images/render_iso.png" alt="PEDAL-256 Isometric View" width="620"> </p> <p align="center"> <em>Figure 1 · Isometric render of the assembled PEDAL-256 pedestal connector.</em> </p> <p align="center"> <a href="LICENSE"><img src="https://img.shields.io/badge/License-CERN--OHL--P_v2-blue.svg"></a> <img src="https://img.shields.io/badge/Hardware-Verified-brightgreen.svg"> <img src="https://img.shields.io/badge/CAD-SolidWorks_2024-red.svg"> <img src="https://img.shields.io/badge/PCB-Altium_%7C_KiCad-orange.svg"> </p>
📖 Overview

PEDAL-256 (Pedestal Elastomeric Dense Array Link) is an open-source, solderless, and scalable pedestal connector system designed for high-density chronic neural recording.
It provides a mechanically robust and electrically reliable interface between thin-film implanted neural probes and external headstages, with a form factor optimized for freely moving animal studies.

The system integrates a high-density interposer PCB, an anisotropic elastomeric contact interface, and a lightweight pedestal housing into a fully integrated, headstage-ready solution.
PEDAL-256 is validated for 256-channel acquisition and architected to support future scaling toward higher channel counts without increasing the volumetric footprint.

The design has been optimized for rats and non-human primates, prioritizing minimal implant mass, mechanical stability, and long-term durability under behavioral conditions.

✨ Key Features

256-Channel High-Density Interface
Compact pedestal footprint supporting up to 256 recording channels.

Solderless Elastomeric Interconnect
Anisotropic conductive elastomer enables repeatable, alignment-tolerant electrical contact without soldering.

Headstage-Ready Integration
Direct compatibility with Intan RHD-series headstages and commutator-based freely moving setups.

Lightweight Mechanical Design
Total assembled mass of approximately 6.4 g, minimizing skull torque during chronic implantation.

Surgical-Grade Pedestal Housing
Textured sidewalls and anchoring features for secure fixation using dental cement or UV-curable resin.

Modular Architecture
Mechanical housing, interposer PCB, and protective cap are separable for rapid iteration, testing, and replacement.

🧩 System Components
<p align="center"> <img src="./images/pedestal-system.jpg" alt="PEDAL-256 System Overview" width="640"> </p>
Component	Description
Housing	3D-printed or machined PEEK pedestal providing mechanical protection and cranial fixation.
Interposer PCB	High-density routing interface connecting thin-film probes to Intan/Omnetics connectors.
Surgical Cap	Protective cap preserving connector integrity throughout the experimental timeline.
📂 Repository Structure
├── CAD/                 # Mechanical design files
│   ├── SolidWorks/      # Native .SLDPRT / .SLDASM files
│   └── STEP/            # Neutral STEP exports
├── PCB/                 # Electrical design files
│   ├── Altium_Designer/ # Source PCB projects
│   ├── KiCad/           # Open-source PCB equivalents
│   ├── Gerbers/         # Manufacturing outputs
│   └── BOM/             # Bill of Materials
├── Docs/                # Documentation
│   ├── Assembly_Guide/  # Step-by-step assembly instructions
│   └── Datasheets/      # Key component datasheets
└── Images/              # Renders and photographs

🛠 Tools Used in Development
Tool	Version	Purpose
SolidWorks	2024	Mechanical design and assembly
Altium Designer	24.0	High-density PCB design
KiCad	8.0.0	Open-source PCB design support
📄 Publication

This work is described in the following publication:

T. Bai et al., “A Scalable, Solderless 256-Channel Pedestal Connector for Thin-Film Neural Interfaces,” IEEE Journal on Flexible Electronics, 2025.
DOI: [to be added]

All design files in this repository correspond directly to the published system.

👥 Developers

Tianyu Bai

Gen Li, Ph.D.

Hui Fang, Ph.D.

Multifunctional Integrated NeuroElectronics (MINE) Lab
Thayer School of Engineering, Dartmouth College
Hanover, NH, USA

📜 License

Copyright © 2025 Tianyu Bai.

This project is released as Open Hardware under the
CERN Open Hardware Licence Version 2 – Permissive (CERN-OHL-P v2).

You may redistribute and modify this design and manufacture products based on it under the terms of the license.
This work is provided without warranty of any kind.
See https://cern.ch/cern-ohl
 for full license text.
