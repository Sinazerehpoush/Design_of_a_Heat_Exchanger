<div align="center">

# Marine Steam Condenser Design & Metallurgical Evaluation
### TEMA AES Configuration | Seawater Cooling & Titanium Optimization

[![Institution - Sharif University of Technology](https://img.shields.io/badge/Sharif_University_of_Technology-Department_of_Mechanical_Engineering-003366?style=for-the-badge&logo=googlescholar&logoColor=white)](http://mech.sharif.edu/)
[![Tool - HTRI Xist](https://img.shields.io/badge/Simulation-HTRI_Xist_v7.3.2-orange?style=for-the-badge&logo=ansys&logoColor=white)](#thermal-hydraulic-design--metallurgical-evaluation)
[![Documentation - LaTeX](https://img.shields.io/badge/Typeset-LaTeX-008080?style=for-the-badge&logo=latex&logoColor=white)](./report/Heat%20Exchanger.tex)
[![Standard - TEMA / HEI](https://img.shields.io/badge/Standard-TEMA_Class_R_%7C_HEI-darkred?style=for-the-badge)](#theoretical-metallurgy--fouling-framework)

<p align="center">
  <b>A comprehensive thermal-hydraulic design and comparative metallurgical evaluation of a 24.0 MW seawater-cooled steam surface condenser using HTRI Xist and MATLAB.</b>
</p>

[View Full Report (PDF)](./report/Design_of_a_Heat_Exchanger.pdf) • [View LaTeX Source](./report/Heat%20Exchanger.tex)

</div>

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

In coastal desalination infrastructure and coastal thermal power generating stations, seawater-cooled surface condensers represent critical thermal nodes governing overall plant efficiency and lifecycle generation costs[cite: 4, 6]. 

* **Duty:** Condense $40{,}198\text{ kg/h}$ of exhaust steam at $154.2^\circ\text{C}$ ($500\text{ kPa}$)[cite: 4, 6].
* **Cooling Medium:** Raw seawater entering at $18.0^\circ\text{C}$ and exiting at $42.5^\circ\text{C}$[cite: 4, 6].
* **Thermal Capacity:** $24.0\text{ MW}$ condensing duty[cite: 4, 6].
* **Configuration:** TEMA AES Type (Removable bonnet, single-pass shell, and floating head with backing device to accommodate thermal expansion gradients $\Delta T = 136.2^\circ\text{C}$)[cite: 4, 6].
* **Validation Tools:** HTRI Xist 7.3.2 and MATLAB[cite: 4, 6].

---

## Theoretical Metallurgy & Fouling Framework

### 1. Degradation and Corrosion Mechanisms: Copper Alloys vs. Titanium
* **Copper-Based Alloys (Aluminum-Brass, Cu-Ni):** Rely on a delicate cuprous oxide ($\text{Cu}_2\text{O}$) passivating film[cite: 4, 6]. Under dynamic seawater turbulence exceeding $\approx 2.0\text{--}3.0\text{ m/s}$, this protective film shears off, triggering accelerated *erosion-corrosion*[cite: 4, 6]. In polluted coastal waters containing dissolved sulfides, copper oxides convert into non-adherent copper sulfides, inducing catastrophic localized pitting[cite: 4, 6].
* **Titanium Grade 2:** Instantly forms a tenacious, self-healing rutile/anatase titanium dioxide ($\text{TiO}_2$) passive layer[cite: 4, 6]. This ceramic-grade film resists dynamic fluid velocities beyond $20\text{ m/s}$, granting complete immunity to pitting, crevice corrosion, and erosion-corrosion[cite: 4, 6].

### 2. Fouling Dynamics and Resistance Mitigation
* **Aluminum-Brass:** Cuprous ions ($\text{Cu}^{2+}$) provide biocidal effects against macro-biological attachment[cite: 4, 6]. However, progressive corrosion forms heavy, porous scale composed of basic copper salts and carbonates, severely impeding conductive heat transfer[cite: 4, 6].
* **Titanium:** Lacks biocidal activity, but features a non-polar, low surface energy state that prevents scale adhesion[cite: 4, 6]. Its superior mechanical strength allows continuous high-velocity flow and mechanical sponge-ball cleaning systems (Taprogge), maintaining an active *self-cleaning* shear effect[cite: 4, 6].

### 3. Critique of Standard TEMA Seawater Fouling Tables
Standard TEMA tables tabulate seawater fouling factors solely as functions of temperature and velocity, ignoring tube metallurgy[cite: 4, 6]. This is flawed because copper tubing actively generates internal scale resistance ($R_f$) through metal corrosion, whereas titanium exhibits near-zero metal loss ($< 0.001\text{ mm/year}$)[cite: 4, 6]. Consequently, specialized standards like **HEI (Heat Exchange Institute)** recommend reducing design fouling resistances by roughly $50\%$ when replacing copper alloys with titanium ($0.00040 \to 0.00018\text{--}0.00020\text{ m}^2\text{K/W}$)[cite: 4, 6].

---

## Exchanger Architecture and Parameter Selection

* **TEMA AES Type:** 
  * *Front Head (Type A):* Removable bonnet providing direct access for mechanical tube cleaning without disconnecting headers[cite: 4, 6].
  * *Shell (Type E):* Standard single-pass crossflow condensing shell[cite: 4, 6].
  * *Rear Head (Type S - Floating Head):* Accommodates severe differential thermal expansion ($\Delta T = 136.2^\circ\text{C}$)[cite: 4, 6].
* **Bundle Layout:** $30^\circ$ Triangular pitch for maximum packing density[cite: 4, 6].
* **Baffling Scheme:** No-Tubes-In-Window (NTIW) segmental baffles with 25% diametral cut and 700 mm spacing to suppress acoustic resonance and crossflow vibration while maintaining shell pressure drop below $25.0\text{ kPa}$[cite: 4, 6].

---

## Thermal-Hydraulic Design & Metallurgical Evaluation

### 1. Material Comparison: Base Aluminum-Brass vs. Standard Titanium
The base unit was designed using Aluminum-Brass ($t_w = 1.245\text{ mm}$)[cite: 4, 6]. Locking the shell envelope ($D_{\text{shell}} = 1168.4\text{ mm}$) in **Rating Mode** evaluated standard Titanium Grade 2 ($t_w = 1.245\text{ mm}$)[cite: 4, 6].

| Design Parameter | Aluminum-Brass (Base) | Titanium Grade 2 (Standard) | Engineering Variation |
| :--- | :---: | :---: | :--- |
| **Execution Mode** | Design Mode | Rating Mode | Fixed Shell Envelope[cite: 4, 6] |
| **Shell Inside Diameter** | 1168.4 mm | 1168.4 mm | Constant[cite: 4, 6] |
| **Total Tube Count ($N_t$)** | **943 tubes** | **1184 tubes** | +25.5% (+241 tubes)[cite: 4, 6] |
| **Tube Passes** | 2 passes | 1 pass | Reconfigured for pressure drop[cite: 4, 6] |
| **Overall $U$ (Actual)** | **1531.2 W/m²·K** | **1210.3 W/m²·K** | -21.0% (Conductivity penalty)[cite: 4, 6] |
| **Tube Metal Resistance** | 1.97% of total $R$ | 7.99% of total $R$ | $\approx 4\times$ increase[cite: 4, 6] |
| **Effective Area ($A$)** | 131.68 m² | 166.23 m² | +26.2% surface expansion[cite: 4, 6] |
| **Tubeside $\Delta P$** | 30.77 kPa | 5.16 kPa | -83.2%[cite: 4, 6] |
| **Overdesign Margin** | 0.92% | 0.90% | Target matched[cite: 4, 6] |

### 2. Optimization via Thin-Wall Titanium ($t_w = 0.559\text{ mm}$)
Leveraging titanium's high tensile strength allows reducing wall thickness to $\sim 0.559\text{ mm}$ ($500\,\mu\text{m}$), cutting wall thermal resistance in half ($7.99\% \to 3.81\%$)[cite: 4, 6]. This saves **108 tubes** compared to standard titanium ($1076\text{ vs. } 1184$)[cite: 4, 6], recovering $45\%$ of the surface penalty while maintaining mechanical integrity[cite: 4, 6].

---

## HTRI Runtime Diagnostics and Vibration Analysis

* **Acoustic Vibration Warning:** Flagged transverse acoustic resonance from vapor vortex shedding; resolved via deresonating baffles at $0.45\times D_{\text{shell}}$[cite: 4, 6].
* **Thermal Conductivity Temperature Limit:** Al-Brass operating temperature slightly exceeded the code database cap ($176.1^\circ\text{F}$); impact on $U$ was negligible ($<0.2\%$ clamped deviation)[cite: 4, 6].
* **Rear Head ID Limitation:** Tight clearance on Type S floating head; deferred to mechanical detailing stage[cite: 4, 6].
* **ASME Section VIII Disclaimer:** Standard notice confirming preliminary thermal estimation weights require structural PVElite validation[cite: 4, 6].

---

## Analytical Validation via MATLAB and Root-Cause Analysis

An in-house 1D thermal resistance model predicted a required tube count of **965 tubes** for thin-wall titanium, exhibiting a **$-10.32\%$ error** compared to HTRI's actual requirement of **1076 tubes**[cite: 4, 6].

* **Root-Cause Diagnosis (Thermal-Hydraulic Feedback):** 
  * Thinning the wall under fixed outer diameter ($19.05\text{ mm}$) expanded the inner diameter ($16.56 \to 17.93\text{ mm}$)[cite: 4, 6].
  * With constant mass flow, seawater bulk velocity dropped ($0.89 \to 0.84\text{ m/s}$)[cite: 4, 6].
  * Because internal heat transfer coefficients follow $h_i \propto V^{0.8}$, the velocity attenuation degraded $h_i$, causing HTRI's actual $U$ to fall to $1334.3\text{ W/m}^2\text{K}$ (whereas MATLAB's constant-$R_{\text{other}}$ assumption overestimated $U$ at $1497.5\text{ W/m}^2\text{K}$)[cite: 4, 6]. This proves tube gauge modifications cannot be modeled as isolated conductive changes[cite: 4, 6].

---

## HTRI Specification Sheets

<div align="center">
  <img src="./Figures/f1.png" alt="Base Al-Brass Sheet" width="85%"/>
  <p><i>Figure 1: Base Aluminum-Brass Design Specification Sheet (943 Tubes).</i></p>
  <br/>
  <img src="./Figures/f2.png" alt="Standard Titanium Sheet" width="85%"/>
  <p><i>Figure 2: Standard-Gauge Titanium Design Specification Sheet (1184 Tubes).</i></p>
  <br/>
  <img src="./Figures/f3.png" alt="Thin-Wall Titanium Sheet" width="85%"/>
  <p><i>Figure 3: Optimized Thin-Wall Titanium Specification Sheet (1076 Tubes).</i></p>
  <br/>
  <img src="./Figures/f4.png" alt="HTRI Runtime Messages" width="85%"/>
  <p><i>Figure 4: HTRI Runtime Messages and Acoustic Vibration Analysis.</i></p>
  <br/>
  <img src="./Figures/f5.png" alt="MATLAB Command Output" width="85%"/>
  <p><i>Figure 5: MATLAB Command Window Output (10.32% Model Discrepancy).</i></p>
</div>

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
│   ├── Design_of_a_Heat_Exchanger.pdf    # Complete compiled technical report
│   └── Heat Exchanger.tex                 # Professional LaTeX source code
│
└── README.md                              # Technical documentation & project summary
