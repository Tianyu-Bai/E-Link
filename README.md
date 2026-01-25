<div align="center">
  <h1 style="border-bottom: none; margin-bottom: 5px;">🚀 PEDAL-256</h1>
  
<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=24&pause=1000&color=00693E&center=true&vCenter=true&width=750&lines=An+Open-Source,+Solderless,+High-Density;Pedestal+Connector+for+Neural+Interfaces" />
</p>


  <p style="margin-top: 15px;">
    <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-red?style=flat-square" alt="License"></a>
    <a href="https://sites.dartmouth.edu/fang-group/"><img src="https://img.shields.io/badge/Dartmouth-MINE--Lab-00693E?style=flat-square" alt="MINE Lab"></a>
    <img src="https://img.shields.io/badge/Verified-256ch-FFA500?style=flat-square" /></a>
    <img src="https://img.shields.io/badge/Copyright-%C2%A9%20Tianyu%20Bai-blue?style=flat-square" alt="Copyright">
    <a href="https://www.linkedin.com/in/tianyubai/"><img src="https://img.shields.io/badge/-LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
  </p>
</div>
  <br />
<div align="center">
  <img src="Videos/Demo new new.gif" 
       alt="PEDAL-256 Assembly Demo GIF" 
       width="750" 
       style="border-radius: 8px; box-shadow: 0 4px 15px rgba(0,0,0,0.1); display: block;">

</div>

## 📖 Overview

**PEDAL-256** (Pedestal Elastomeric Dense Array Link) is an open-source, solderless, and scalable pedestal connector system designed for high-density chronic neural recording. It provides a mechanically robust and electrically reliable interface between thin-film implanted neural probes and external headstages, with a form factor optimized for freely moving animal studies.

> [!Note]
> **Key Innovation:** The system integrates a high-density interposer PCB, an anisotropic elastomeric contact interface, and a lightweight pedestal housing into a fully integrated, headstage-ready solution.

### 📊 Quick Specifications

| Specification | PEDAL-256_V1.1 |
| :--- | :--- |
| **Channel Count** | 128 or 256 Channels (Single/Dual SPI Port support) |
| **Total Mass** | ~6.6 g (with housing)<br>~2.8 g (without housing) |
| **Interconnect Type** | Solderless Anisotropic Elastomer |
| **Compatible Acquisition System** | Intan Recording Controller (512ch or 1024ch)<br>Open-Ephys acquisition box<br>NeuroNexus Smartbox |
| **Housing Material** | 3D-Printed PEEK / Surgical Grade Resin |

---

## ✨ Key Features

* **⚡ 256-Channel High-Density Interface**
    Compact pedestal footprint supporting high-density acquisition without increasing surgical overhead.
* **🔌 Solderless Elastomeric Interconnect**
    Uses anisotropic conductive elastomer for repeatable, alignment-tolerant electrical contact.
* **🐭 Optimized for In-Vivo Research**
   Minimal Implant Footprint Core components weigh only 2.8g (with housing removed), reducing head-heavy behavior and improving animal welfare during long-term recording sessions.
* **🛠️ Modular & Scalable**
    Separable housing, PCB, and protective cap for rapid iteration and troubleshooting.
* **🧪 Surgical-Grade Design**
    Textured sidewalls for superior adhesion with dental cement or UV-curable resin.
<div align="center">
  <br />
  <img src="Videos/Animation repeat.gif" 
       alt="PEDAL-256 Animation GIF" 
       width="500" 
       style="border-radius: 6px; box-shadow: 0 2px 10px rgba(0,0,0,0.1); display: block;">
</div>

## 🧩 System Components
<div align="center">
<p align="center">

| Component | Description |
| :--- | :--- |
| **Pedestal Housing** | 3D-printed/machined pedestal providing structural support and cranial fixation. |
| **Customized 256Ch Headstage** | Form-factor optimized recording interface for high-density 128/256-channel signal acquisition. |
| **Foam Washer** | Provides compliant compression to ensure uniform electrical contact across the elastomeric interface. |
| **Adapter PCB** | High-density interposer PCB for routing signals from thin-film probes to standardized connector arrays. |
| **Surgical Cap** | Protective enclosure preserving electrical and mechanical integrity throughout chronic experiments. |

  <img src="Images/001.PNG" alt="PEDAL-256 Exploded View" width="750">

  <p style="margin-top: 5px; font-size: 0.95em; color: #333;">
    <b> Mating Dynamics (left) and Structural Breakdown (right) of the PEDAL-256</b>
  </p>
</div>

### 🧩 Bill of Materials (BOM) of the headstage

| Component | Part Number / Description | Qty | Package | Notes |
| :--- | :--- | :--- | :--- | :--- |
| **Amplifier IC** | Intan RHD2164 | 4 | BGA | **Critical:** Ensure correct orientation |
| **SPI Connector** | Omnetics A7621 | 2 | - | 12-wire cable harness (32 AWG) |
| **Resistors** | Standard SMD | 7 | 0402 | - |
| **Capacitors** | Standard SMD | 8 | 0603 | - |
| **Power LED** | Green LED | 1 | 0402 | Power Indicator |
| **Solder Balls** | 0.4 mm Lead-free | ~300 | - | For BGA rework/assembly |


## 👥 Developers & Lab
This project is developed by the Multifunctional Integrated NeuroElectronics (MINE) Lab at Dartmouth College.

Tianyu Bai - Lead Designer

Gen Li, Ph.D.

Yongli Qi, Ph.D.

Hui Fang, Ph.D. - Principal Investigator

<p align="left">
  <a href="[https://engineering.dartmouth.edu/research/labs/multifunctional-integrated-neuroelectronics-lab](https://sites.dartmouth.edu/fang-group/)">
    <img src="https://img.shields.io/badge/Dartmouth-MINE--Lab-00693E?style=flat-square" alt="MINE Lab">
  </a>
</p>

## 📑 Citation & Feedback

For academic use, please cite this repository until our formal publication is released. We also welcome feedback and collaboration from the neuroengineering community!

- **Current Reference:** PEDAL-256 Open Source Hardware (v1.0), MINE Lab, Dartmouth College.

## 📄 Publication

This work is currently **under review**. 

The hardware designs and visual assets in this repository correspond directly to the system described in our submitted manuscript. To maintain the integrity of the peer-review process:
* **Full Citation:** Will be updated here upon formal acceptance.
* **Inquiries:** For access to the full manuscript or questions regarding the design, please contact **Tianyu Bai** or **Prof. Hui Fang**.
- **Full Paper:** *Coming Soon.*
---

## 🤝 Acknowledgments

The developers gratefully acknowledge support from the **NIH (R01MH139342)** and the **Dartmouth PhD Innovation Fellowship**. 

Special thanks to the members of the **MINE Lab** and the **Thayer School of Engineering** for their technical support and feedback throughout the development of the PEDAL-256 system.

## 📜 License
Copyright © 2026 Tianyu Bai. Copyright © 2026 Tianyu Bai. This project is licensed under the MIT License. See the LICENSE file for details.
