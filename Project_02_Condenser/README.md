<div align="center">

# Marine Steam Condenser Design & Metallurgical Evaluation
### TEMA AES Configuration | Seawater Cooling & Titanium Optimization

[![Institution - Sharif University of Technology](https://img.shields.io/badge/Sharif_University_of_Technology-Department_of_Mechanical_Engineering-003366?style=for-the-badge&logo=googlescholar&logoColor=white)](http://mech.sharif.edu/)
[![Tool - HTRI Xist](https://img.shields.io/badge/Simulation-HTRI_Xist_v7.3.2-orange?style=for-the-badge&logo=ansys&logoColor=white)](#thermal-hydraulic-design--metallurgical-evaluation)
[![Documentation - LaTeX](https://img.shields.io/badge/Typeset-LaTeX-008080?style=for-the-badge&logo=latex&logoColor=white)](./report/Mbaddel_project_2.tex)
[![Standard - TEMA / HEI](https://img.shields.io/badge/Standard-TEMA_Class_R_%7C_HEI-darkred?style=for-the-badge)](#introduction-and-theoretical-metallurgy-framework)

<p align="center">
  <b>A comprehensive thermal-hydraulic design and comparative metallurgical evaluation of a 24.0 MW seawater-cooled steam surface condenser using HTRI Xist and MATLAB.</b>
</p>

[View Full Report (PDF)](./report/Design_of_a_Heat_Exchanger.pdf) • [View LaTeX Source](./report/Heat%20Exchanger.tex)</div>

---

## Table of Contents
- [Project Overview](#project-overview)
- [Theoretical Metallurgy & Fouling Framework](#theoretical-metallurgy--fouling-framework)
  - [Corrosion Mechanisms](#1-degradation-and-corrosion-mechanisms-copper-alloys-vs-titanium)
  - [Fouling Dynamics](#2-fouling-dynamics-and-resistance-mitigation)
  - [Critique of TEMA Standards](#3-critique-of-standard-tema-seawater-fouling-tables)
- [Exchanger Architecture](#exchanger-architecture-and-parameter-selection)
- [Thermal-Hydraulic Design & Optimization](#thermal-hydraulic-design--metallurgical-evaluation)
  - [Aluminum-Brass vs. Standard Titanium](#1-material-comparison-base-aluminum-brass-vs-standard-titanium)
  - [Thin-Wall Titanium Optimization](#2-optimization-via-thin-wall-titanium-tw--0559-mm)
- [HTRI Runtime Diagnostics & Vibration Analysis](#htri-runtime-diagnostics-and-vibration-analysis)
- [Analytical MATLAB Model & Hydraulic Root-Cause Analysis](#analytical-validation-via-matlab-and-root-cause-analysis)
- [HTRI Specification Sheets](#htri-specification-sheets)
- [Repository Structure](#repository-structure)

---

## Project Overview

In coastal desalination infrastructure and coastal thermal power generating stations, seawater-cooled surface condensers represent critical thermal nodes governing overall plant efficiency and lifecycle generation costs. 

* **Duty:** Condense $40{,}198\text{ kg/h}$ of exhaust steam at $154.2^\circ\text{C}$ ($500\text{ kPa}$).
* **Cooling Medium:** Raw seawater entering at $18.0^\circ\text{C}$ and exiting at $42.5^\circ\text{C}$.
* **Thermal Capacity:** $24.0\text{ MW}$ condensing duty.
* **Configuration:** TEMA AES Type (Removable bonnet, single-pass shell, and floating head with backing device to accommodate thermal expansion gradients $\Delta T = 136.2^\circ\text{C}$).
* **Validation Tools:** HTRI Xist 7.3.2 and MATLAB.

---

## Theoretical Metallurgy & Fouling Framework

### 1. Degradation and Corrosion Mechanisms
* **Copper-Based Alloys (Aluminum-Brass, Cu-Ni):** Rely on a delicate cuprous oxide ($\text{Cu}_2\text{O}$) passivating film. Under dynamic seawater turbulence exceeding $\approx 2.0\text{--}3.0\text{ m/s}$, this protective film shears off, triggering accelerated *erosion-corrosion*. In polluted coastal waters containing dissolved sulfides, copper oxides convert into non-adherent copper sulfides, inducing catastrophic localized pitting.
* **Titanium Grade 2:** Instantly forms a tenacious, self-healing rutile/anatase titanium dioxide ($\text{TiO}_2$) passive layer. This ceramic-grade film resists dynamic fluid velocities beyond $20\text{ m/s}$, granting complete immunity to pitting, crevice corrosion, and erosion-corrosion.

### 2. Fouling Dynamics & Resistance Mitigation
* **Aluminum-Brass:** Cuprous ions ($\text{Cu}^{2+}$) provide biocidal effects against macro-biological attachment. However, progressive corrosion forms heavy, porous scale composed of basic copper salts and carbonates, severely impeding conductive heat transfer.
* **Titanium:** Lacks biocidal activity, but features a non-polar, low surface energy state that prevents scale adhesion. Its superior mechanical strength allows continuous high-velocity flow and mechanical sponge-ball cleaning systems (Taprogge), maintaining an active *self-cleaning* shear effect.

### 3. Critique of Standard TEMA Seawater Fouling Tables
Standard TEMA tables tabulate seawater fouling factors solely as functions of temperature and velocity, ignoring tube metallurgy. This is flawed because copper tubing actively generates internal scale resistance ($R_f$) through metal corrosion, whereas titanium exhibits near-zero metal loss ($< 0.001\text{ mm/year}$). Consequently, specialized standards like **HEI (Heat Exchange Institute)** recommend reducing design fouling resistances by roughly $50\%$ when replacing copper alloys with titanium ($0.00040 \to 0.00018\text{--}0.00020\text{ m}^2\text{K/W}$).

---

## Exchanger Architecture and Parameter Selection

* **TEMA AES Type:** 
  * *Front Head (Type A):* Removable bonnet providing direct access for mechanical tube cleaning without disconnecting headers.
  * *Shell (Type E):* Standard single-pass crossflow condensing shell.
  * *Rear Head (Type S - Floating Head):* Accommodates severe differential thermal expansion ($\Delta T = 136.2^\circ\text{C}$).
* **Bundle Layout:** $30^\circ$ Triangular pitch for maximum packing density.
* **Baffling Scheme:** No-Tubes-In-Window (NTIW) segmental baffles with 25% diametral cut and 700 mm spacing to suppress acoustic resonance and crossflow vibration while maintaining shell pressure drop below $25.0\text{ kPa}$.

---

## Thermal-Hydraulic Design & Metallurgical Evaluation

### 1. Material Comparison: Base Aluminum-Brass vs. Standard Titanium
The base unit was designed using Aluminum-Brass ($t_w = 1.245\text{ mm}$). Locking the shell envelope ($D_{\text{shell}} = 1168.4\text{ mm}$) in **Rating Mode** evaluated standard Titanium Grade 2 ($t_w = 1.245\text{ mm}$).

| Design Parameter | Aluminum-Brass (Base) | Titanium Grade 2 (Standard) | Engineering Variation |
| :--- | :---: | :---: | :--- |
| **Execution Mode** | Design Mode | Rating Mode | Fixed Shell Envelope |
| **Shell Inside Diameter** | 1168.4 mm | 1168.4 mm | Constant |
| **Total Tube Count ($N_t$)** | **943 tubes** | **1184 tubes** | +25.5% (+241 tubes) |
| **Tube Passes** | 2 passes | 1 pass | Reconfigured for pressure drop |
| **Overall $U$ (Actual)** | **1531.2 W/m²·K** | **1210.3 W/m²·K** | -21.0% (Conductivity penalty) |
| **Tube Metal Resistance** | 1.97% of total $R$ | 7.99% of total $R$ | $\approx 4\times$ increase |
| **Effective Area ($A$)** | 131.68 m² | 166.23 m² | +26.2% surface expansion |
| **Tubeside $\Delta P$** | 30.77 kPa | 5.16 kPa | -83.2% |
| **Overdesign Margin** | 0.92% | 0.90% | Target matched |

### 2. Optimization via Thin-Wall Titanium ($t_w = 0.559\text{ mm}$)
Leveraging titanium's high tensile strength allows reducing wall thickness to $\sim 0.559\text{ mm}$ ($500\,\mu\text{m}$), cutting wall thermal resistance in half ($7.99\% \to 3.81\%$). This saves **108 tubes** compared to standard titanium ($1076\text{ vs. } 1184$), recovering $45\%$ of the surface penalty while maintaining mechanical integrity.

---

## HTRI Runtime Diagnostics & Vibration Analysis

* **Acoustic Vibration Warning:** Flagged transverse acoustic resonance from vapor vortex shedding; resolved via deresonating baffles at $0.45\times D_{\text{shell}}$.
* **Thermal Conductivity Temperature Limit:** Al-Brass operating temperature slightly exceeded the code database cap ($176.1^\circ\text{F}$); impact on $U$ was negligible ($<0.2\%$ clamped deviation).
* **Rear Head ID Limitation:** Tight clearance on Type S floating head; deferred to mechanical detailing stage.
* **ASME Section VIII Disclaimer:** Standard notice confirming preliminary thermal estimation weights require structural PVElite validation.

---

## Analytical MATLAB Model & Hydraulic Root-Cause Analysis

An in-house 1D thermal resistance model predicted a required tube count of **965 tubes** for thin-wall titanium, exhibiting a **$-10.32\%$ error** compared to HTRI's actual requirement of **1076 tubes**.

* **Root-Cause Diagnosis (Thermal-Hydraulic Feedback):** 
  * Thinning the wall under fixed outer diameter ($19.05\text{ mm}$) expanded the inner diameter ($16.56 \to 17.93\text{ mm}$).
  * With constant mass flow, seawater bulk velocity dropped ($0.89 \to 0.84\text{ m/s}$).
  * Because internal heat transfer coefficients follow $h_i \propto V^{0.8}$, the velocity attenuation degraded $h_i$, causing HTRI's actual $U$ to fall to $1334.3\text{ W/m}^2\text{K}$ (whereas MATLAB's constant-$R_{\text{other}}$ assumption overestimated $U$ at $1497.5\text{ W/m}^2\text{K}$). This proves tube gauge modifications cannot be modeled as isolated conductive changes.

---

## HTRI Specification Sheets & Reports

* **Base Al-Design Sheet:** `./Figures/f1.png`
* **Standard Titanium Sheet:** `./Figures/f2.png`
* **Thin-Wall Titanium Sheet:** `./Figures/f3.png`
* **HTRI Runtime Diagnostics:** `./Figures/f4.png`
* **MATLAB Command Output:** `./Figures/f5.png`

---

## Repository Structure

```text
Project_02_Condenser/
│
├── Figures/                               # HTRI specification sheets & MATLAB plots
│   ├── f1.png                             # Base Aluminum-Brass TEMA Sheet
│   ├── f2.png                             # Standard-Gauge Titanium TEMA Sheet
│   ├── f3.png                             # Thin-Wall Titanium TEMA Sheet
│   ├── f4.png                             # HTRI Runtime Messages Report
│   └── f5.png                             # MATLAB Analytical Output Window
│
├── report/
│   ├── Mbaddel_project_2.pdf              # Complete compiled technical report
│   └── Mbaddel_project_2.tex              # Professional LaTeX source code
│
└── README.md                              # Technical documentation & project summary
