<div align="center">

# 🏭 Industrial Reboiler Heat Exchanger Design & Debottlenecking
### TEMA BEM Configuration | Sour Hydrocarbon Vaporization

[![Institution - Sharif University of Technology](https://img.shields.io/badge/Sharif_University_of_Technology-Department_of_Mechanical_Engineering-003366?style=for-the-badge&logo=googlescholar&logoColor=white)](http://mech.sharif.edu/)
[![Tool - HTRI Xist](https://img.shields.io/badge/Simulation-HTRI_Xist_v7.3.2-orange?style=for-the-badge&logo=ansys&logoColor=white)](#summary-of-thermal-hydraulic-performance)
[![Documentation - LaTeX](https://img.shields.io/badge/Typeset-LaTeX-008080?style=for-the-badge&logo=latex&logoColor=white)](./Heat_Exchanger.tex)
[![Standard - TEMA / ASME](https://img.shields.io/badge/Standard-TEMA_Class_R_%7C_ASME_VIII-darkred?style=for-the-badge)](#engineering-decisions--basis-of-design)

<p align="center">
  <b>A rigorous thermal-hydraulic design and debottlenecking analysis for a shell-and-tube reboiler in the gas sweetening plant of Ilam Gas Refinery.</b>
</p>

[📄 View Full Report (PDF)](./Design_of_a_Heat_Exchanger.pdf) • [📝 View LaTeX Source](./Heat_Exchanger.tex) • [📊 Base TEMA Sheet](#base-case-specification-sheet) • [📈 Debottlenecked TEMA Sheet](#debottlenecked-case-specification-sheet)

</div>

---

## 📑 Table of Contents
- [Project Overview](#project-overview)
- [Engineering Decisions & Basis of Design](#engineering-decisions--basis-of-design)
  - [Fluid Allocation](#1-fluid-allocation-justification)
  - [Exchanger Architecture](#2-exchanger-architecture-tema-bem)
  - [Metallurgy & Geometry](#3-metallurgy--geometry)
- [Summary of Thermal-Hydraulic Performance](#summary-of-thermal-hydraulic-performance)
- [Non-Linear Scaling: Area vs. Throughput](#non-linear-scaling-area-vs-throughput)
- [HTRI Runtime Messages & Engineering Resolutions](#htri-runtime-messages--engineering-resolutions)
- [HTRI Specification Sheets](#htri-specification-sheets)
  - [Base Case Specification Sheet](#base-case-specification-sheet)
  - [Debottlenecked Case Specification Sheet](#debottlenecked-case-specification-sheet)
- [Repository Structure](#repository-structure)

---

## 📌 Project Overview

In natural gas sweetening units, thermal energy must be continuously supplied to the bottom of the regenerator stripper to liberate acid gases ($\text{CO}_2$, $\text{H}_2\text{S}$) and regenerate lean amine[cite: 5, 6]. 

* **Duty:** Vaporize a ternary, highly corrosive process mixture consisting of **50 wt% Water, 25 wt% Ammonia, and 25 wt% Benzene** from $x_{\text{in}} = 0.0$ to $x_{\text{out}} = 0.50$[cite: 5, 6].
* **Heating Medium:** Low-Pressure Utility Steam (LP-Steam) condensing from $x_{\text{in}} = 1.0$ to saturated condensate $x_{\text{out}} = 0.0$[cite: 5, 6].
* **Target Throughput:** Base operation at **25,000 kg/hr** (3.41 MW) with debottlenecking capability up to **30,000 kg/hr** (4.09 MW, $+20\%$ capacity expansion)[cite: 5, 6].
* **Validation:** Verified against [TEMA Class R](https://tema.org/) standards and modeled via [HTRI Xchanger Suite](https://www.htri.net/)[cite: 5, 6].

---

## ⚙️ Engineering Decisions & Basis of Design

### 1. Fluid Allocation Justification
* **Tubeside $\to$ Process Stream:**
  * **Corrosion Control:** The fluid contains 25% Ammonia ($\text{NH}_3$)[cite: 5, 6]. Allocating this fluid inside the tubes allows localized use of austenitic **Stainless Steel 304 (18Cr, 8Ni)** tubing, preventing the prohibitive expense of fabricating a high-alloy shell vessel[cite: 5, 6].
  * **Pressure Containment:** Operating pressure tubeside ($7.0\text{ bar}$) is double the shell pressure ($3.5\text{ bar}$)[cite: 5, 6]. Flowing the high-pressure stream tubeside significantly reduces shell thickness and vessel weight[cite: 5, 6].
* **Shellside $\to$ LP-Steam Utility:**
  * Clean, non-fouling condensing steam ($R_f = 0.00018\text{ m}^2\text{K/W}$) across horizontal tube bundles delivers an exceptionally high outer convective film coefficient ($h_o \approx 16{,}000\text{ W/m}^2\text{K}$)[cite: 5, 6].

### 2. Exchanger Architecture (TEMA BEM)
* **Front Head (Type B - Bonnet):** Economical and rigid closure. Frequent internal physical cleaning of tubes is unnecessary in continuous sour service; chemical cleaning is preferred[cite: 5, 6].
* **Shell (Type E - One-Pass):** Classic single-pass arrangement providing optimal counter-current crossflow[cite: 5, 6].
* **Rear Head (Type M - Fixed Tubesheet):** Fixed tubesheets feature the lowest capital cost[cite: 5, 6]. Most importantly, eliminating internal floating-head packings removes any risk of toxic $\text{NH}_3$ / Benzene leakage into the plant utility steam condensate line[cite: 5, 6].

### 3. Metallurgy & Geometry
* **Tube Metallurgy:** Austenitic Stainless Steel 304. *Note: Strictly excludes all copper-based alloys (e.g., admiralty brass, naval brass) due to catastrophic ammonia stress-corrosion cracking (SCC).*[cite: 5, 6]
* **Shell Metallurgy:** Structural Carbon Steel[cite: 5, 6].
* **Tube Dimensions:** $\text{OD} = 22.225\text{ mm}$ ($7/8\text{ in}$), wall thickness $t_w = 2.108\text{ mm}$, active length $L = 6.706\text{ m}$[cite: 5, 6].
* **Bundle Layout:** $30^\circ$ Triangular pitch ($\text{Pitch Ratio} = 1.33$, $\text{Pitch} = 29.56\text{ mm}$) to yield maximum heat transfer area per unit shell diameter[cite: 5, 6].
* **Baffling:** Single-segmental carbon steel baffles with 25% diametral cut and 233 mm spacing (24 crosspasses)[cite: 5, 6].

---

## 📊 Summary of Thermal-Hydraulic Performance

The exchanger was designed in **Design Mode** for baseline throughput and subsequently evaluated in **Rating Mode** for capacity expansion (+20% mass flow)[cite: 5, 6].

| Design Parameter | Units | Baseline Case (25,000 kg/hr) | Debottlenecked Case (30,000 kg/hr) | Engineering Assessment |
| :--- | :---: | :---: | :---: | :--- |
| **Thermal Duty ($Q$)** | MW | **3.407**[cite: 5, 6] | **4.086**[cite: 5, 6] | +19.9% (Directly proportional to flow)[cite: 5, 6] |
| **Shell Inside Diameter** | mm | **584.20**[cite: 5, 6] | **635.00**[cite: 5, 6] | Scaled to house expanded tube bundle[cite: 5, 6] |
| **Total Tube Count ($N_t$)** | — | **285**[cite: 5, 6] | **333**[cite: 5, 6] | +16.8% tube count expansion[cite: 5, 6] |
| **Tube Passes** | — | **2 passes**[cite: 5, 6] | **2 passes**[cite: 5, 6] | Preserves core turbulence & velocity[cite: 5, 6] |
| **Overall $U$ (Actual)** | W/m²·K | **814.46**[cite: 5, 6] | **823.49**[cite: 5, 6] | +1.1% enhancement via higher *Re*[cite: 5, 6] |
| **Required Service $U$** | W/m²·K | **683.40**[cite: 5, 6] | **698.71**[cite: 5, 6] | Governed by fouling safety factors[cite: 5, 6] |
| **Effective Heat Transfer Area** | m² | **131.04**[cite: 5, 6] | **152.97**[cite: 5, 6] | Sub-linear area requirement (+16.7%)[cite: 5, 6] |
| **Tubeside $\Delta P$ (Calc / Allow)** | kPa | **19.99** / 30.00[cite: 5, 6] | **21.56** / 30.00[cite: 5, 6] | Well within allowable limits[cite: 5, 6] |
| **Shellside $\Delta P$ (Calc / Allow)** | kPa | **12.97** / 30.00[cite: 5, 6] | **11.57** / 30.00[cite: 5, 6] | Hydraulic margins preserved[cite: 5, 6] |
| **Overdesign Margin** | % | **19.18%**[cite: 5, 6] | **17.86%**[cite: 5, 6] | High operational safety buffer[cite: 5, 6] |

---

## 📈 Non-Linear Scaling: Area vs. Throughput

A fundamental question addressed in this design is whether surface area requirements scale linearly with flow rate (+20% flow vs. +20% area)[cite: 5, 6].

$$Q = U \cdot A \cdot \Delta T_{\text{LM}}$$
[cite: 5, 6]

1. Scaling mass throughput by 20% proportionally elevates total vaporization duty: $\Delta Q \approx +20\%$[cite: 5, 6].
2. Higher flow elevates tubeside mass velocity, directly boosting the **Reynolds number ($Re$)**[cite: 5, 6].
3. In forced convective two-phase boiling, the convective coefficient follows $h_i \propto Re^{0.8}$[cite: 5, 6]. The tubeside film coefficient rises from 2971.9 W/m²·K to 3078.6 W/m²·K, driving overall clean and actual $U$ upward (814.5 $\to$ 823.5 W/m²·K)[cite: 5, 6].
4. Because the overall heat transfer coefficient improves dynamically, the required heat transfer surface area scales **sub-linearly**[cite: 5, 6]:

$$\frac{dA}{d\dot{m}} < \frac{A_0}{\dot{m}_0} \quad \implies \quad \Delta A = +16.74\% \quad \text{for} \quad \Delta \dot{m} = +20.0\%$$
[cite: 5, 6]

---

## 🛠️ HTRI Runtime Messages & Engineering Resolutions

During iterative convergence in HTRI Xist, several warnings were addressed[cite: 5, 6]:

* ⚠️ **Terminal Temperature Inconsistency (`Run Failed`):**  
  * *Root Cause:* Mismatch in equilibrium flash curves and inconsistent pressure conversions[cite: 5, 6].  
  * *Resolution:* Standardized operating pressure boundary conditions in absolute Pascal units and aligned inlet flash conditions[cite: 5, 6].
* ⚠️ **Wavy Stratified Flow & Upper Surface Dryout:**  
  * *Root Cause:* Low liquid mass flux inside single-pass horizontal tubes causes gravity separation of vapor and liquid, leading to dryout at upper wall perimeters[cite: 5, 6].  
  * *Resolution:* Adopted a **2-pass tube layout**[cite: 5, 6]. Increased mixture velocity enforced dispersed annular flow, eliminating dryout warnings[cite: 5, 6].
* ⚠️ **Shellside Inlet Kinetic Momentum ($\rho V^2 > 1000\text{ kg/m}\cdot\text{s}^2$):**  
  * *Root Cause:* Inlet LP-steam nozzle jet velocity produced $\rho V^2 = 1199.8\text{ kg/m}\cdot\text{s}^2$, posing flow-induced tube vibration and erosion threats[cite: 5, 6].  
  * *Resolution:* Integrated shell inlet **Impingement Rods** and adjusted bundle entrance ratios in accordance with TEMA Section 5[cite: 5, 6].
* ⚠️ **Transition Boiling Increment Warning:**  
  * *Analysis:* Localized transitions between nucleate and film boiling were reported[cite: 5, 6]. Because overall EMTD is moderate ($\approx 38^\circ\text{C}$), peak local fluxes remain well beneath Critical Heat Flux ($q'' < q''_{\text{CHF}}$), ensuring thermal stability[cite: 5, 6].

---

## 📑 HTRI Specification Sheets

### 🔹 Base Case Specification Sheet
*(Throughput: 25,000 kg/hr | Heat Duty: 3.41 MW | 285 Tubes)*[cite: 5, 6]

<div align="center">
  <img src="./figures/f1.png" alt="HTRI Base Case TEMA Sheet" width="85%"/>
</div>

---

### 🔹 Debottlenecked Case Specification Sheet
*(Throughput: 30,000 kg/hr | Heat Duty: 4.09 MW | 333 Tubes)*[cite: 5, 6]

<div align="center">
  <img src="./figures/f2.png" alt="HTRI Debottlenecked Case TEMA Sheet" width="85%"/>
</div>

---

## 📁 Repository Structure

```text
Project_01_Reboiler/
│
├── figures/                               # Simulation data sheets & plots
│   ├── f1.png                             # HTRI Specification Sheet (Base Case)
│   ├── f2.png                             # HTRI Specification Sheet (Debottlenecked Case)
│   ├── f3.png                             # HTRI Base Case Output Summary
│   └── f4.png                             # HTRI Debottlenecked Output Summary
│
├── Design_of_a_Heat_Exchanger.pdf         # Complete compiled technical report
├── Heat_Exchanger.tex                     # Professional LaTeX source code
└── README.md                              # Technical documentation & project portfolio
