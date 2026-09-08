<div align="center">

# Heat Exchanger Design & Thermal-Hydraulic Portfolio
### Sharif University of Technology — Department of Mechanical Engineering

[![Institution - Sharif University of Technology](https://img.shields.io/badge/Sharif_University_of_Technology-Department_of_Mechanical_Engineering-003366?style=for-the-badge&logo=googlescholar&logoColor=white)](http://mech.sharif.edu/)
[![Simulation - HTRI Xist](https://img.shields.io/badge/Simulation-HTRI_Xist_v7.3.2-orange?style=for-the-badge&logo=ansys&logoColor=white)](https://github.com/Sinazerehpoush/Design_of_a_Heat_Exchanger)
[![Documentation - LaTeX](https://img.shields.io/badge/Typeset-LaTeX-008080?style=for-the-badge&logo=latex&logoColor=white)](https://github.com/Sinazerehpoush/Design_of_a_Heat_Exchanger)
[![Standard - TEMA / ASME / HEI](https://img.shields.io/badge/Standard-TEMA_R%2FE_%7C_ASME_VIII_%7C_HEI-darkred?style=for-the-badge)](https://github.com/Sinazerehpoush/Design_of_a_Heat_Exchanger)

<p align="center">
  <b>A comprehensive professional portfolio featuring rigorous thermal-hydraulic design, rating, debottlenecking, and metallurgical optimization of shell-and-tube heat exchangers.</b>
</p>

</div>

---

## Portfolio Overview

This repository contains advanced thermal-hydraulic engineering design projects executed using **HTRI Xist**, **MATLAB**, and **LaTeX**. Each project covers complete process specifications, code-compliant mechanical considerations (TEMA, ASME, HEI), runtime diagnostic resolutions, and automated analytical validations.

---

## Projects Directory

### 1. Industrial Reboiler Heat Exchanger Design & Debottlenecking
* **Configuration:** TEMA BEM | Sour Hydrocarbon Vaporization
* **Application:** Gas sweetening plant of Ilam Gas Refinery (Vaporizing a ternary mixture of Water, Ammonia, and Benzene).
* **Key Highlights:**
  * Rigorous design for baseline duty ($3.41\text{ MW}$) and debottlenecking capacity expansion up to $+20\%$ ($4.09\text{ MW}$).
  * Fluid allocation strategy optimizing stainless steel metallurgy for ammonia corrosion control.
  * Resolution of two-phase flow instabilities, terminal temperature inconsistencies, and shellside inlet momentum limits ($\rho V^2$).
  * Non-linear area scaling analysis ($dA/d\dot{m} < A_0/\dot{m}_0$) driven by forced convective boiling enhancement ($h_i \propto Re^{0.8}$).
* **[📁 Explore Project 1 Directory](./Project_01_Reboiler/)**

### 2. Marine Steam Condenser Design & Metallurgical Evaluation
* **Configuration:** TEMA AES | Seawater Cooling & Titanium Optimization
* **Application:** Coastal desalination infrastructure and thermal power generating stations ($24.0\text{ MW}$ surface condenser).
* **Key Highlights:**
  * Comparative metallurgical evaluation between base Aluminum-Brass and Titanium Grade 2.
  * Rigorous critique of standard TEMA seawater fouling tables versus HEI standards.
  * Thin-wall titanium optimization ($t_w = 0.559\text{ mm}$), securing a 108-tube reduction and halving metal wall resistance.
  * Analytical MATLAB 1D thermal resistance modeling and root-cause identification of a $10.3\%$ sizing discrepancy driven by internal velocity attenuation and convective feedback ($h_i \propto V^{0.8}$).
* **[📁 Explore Project 2 Directory](./Project_02_Condenser/)**

---

## Technical Stack & Standards

* **Thermal Simulation & Rating:** HTRI Xchanger Suite (v7.3.2)
* **Numerical & Analytical Modeling:** MATLAB (Object-oriented 1D resistance algorithms)
* **Typesetting & Documentation:** LaTeX (Professional academic reports with TikZ and PGFplots)
* **Governing Codes & Standards:** 
  * Tubular Exchanger Manufacturers Association (TEMA Class R & E)
  * American Society of Mechanical Engineers (ASME Boiler and Pressure Vessel Code, Section VIII Div. 1)
  * Heat Exchange Institute (HEI Standards for Steam Surface Condensers)

---

<div align="center">
  <b>Author:</b> Sina Zerehposh • Department of Mechanical Engineering, Sharif University of Technology
</div>
