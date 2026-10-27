# RegoMelt: Lunar Regolith Microwave Sintering Complex Impedance Auditor

[Explore Live Interactive Digital Twin](https://msamsonov1.github.io/regolith-impedance-sintering-sim/) | **NASA SBIR/STTR Topic: TX07.01 / TX12.01** | **Proprietary Notice**

A real-time closed-loop multi-physics digital twin and high-temperature complex impedance auditor for 2.45 GHz microwave sintering of in-situ lunar regolith into structural ceramics exceeding 30 MPa compressive strength.

---

## Executive Overview

Artemis surface permanence requires scalable in-situ manufacturing of launch and landing pads, blast deflection berms, and radiation-shielded habitat blocks without hauling heavy payload mass from Earth. However, raw lunar regolith under hard vacuum has an extremely low thermal conductivity:

$$k \approx 0.002 \text{ to } 0.01 \text{ W} / (\text{m} \cdot \text{K})$$

Traditional radiative and conductive surface heating inevitably causes surface vitrification and volatile boil-off before the brick interior can consolidate.

RegoMelt utilizes microwave volumetric heating driven by sub-micron nanophase metallic iron ($\text{np-Fe}^0$) embedded inside lunar impact agglutinates. As the regolith heats and grain boundaries fuse into dense basaltic glass ($> 2.85 \text{ g/cm}^3$), its microwave power dissipation evolves dynamically:

$$P_{\text{diss}} = 2\pi f \cdot \varepsilon_0 \cdot \varepsilon' \cdot \tan(\delta) \cdot |E_{\text{RMS}}|^2$$

### The Core Problem Solved: The "Z-Stall"

During open-loop microwave sintering, internal volatile degassing pockets and differential thermal gradients form hollow cavities that halt dielectric densification—a condition termed a **Z-Stall**. Existing hardware fails to catch this in real time, yielding structural blocks riddled with hidden internal microcracks.

RegoMelt audits the complex impedance trajectory $Z(E)$ along its non-linear sigmoidal decline, dynamically modulating magnetron duty cycles and phase shifters to collapse internal voids before micro-fractures nucleate.

---

## Key Capabilities

* **3D Electromagnetic Cavity Simulation (Three.js):** Real-time spatial tracking of 2.45 GHz multi-mode standing wave nodes, localized volumetric heating cores, and workpiece consolidation.
* **Live (E, Z) S-Curve Tracking (Chart.js):** Dynamic plotting of real-time complex impedance decay from unconsolidated powder ($Z \approx 1250 \ \Omega$) down to dense basalt ceramic ($Z \approx 85 \ \Omega$).
* **Closed-Loop Anomaly Mitigation:**
  * **Void Degas Detection (Z-Stall):** Dynamically throttles and pulses RF duty cycles to allow degassing channels to collapse without thermal shock.
  * **Thermal Runaway Suppression:** Quenches high-temperature loss-tangent spikes before structural vaporization occurs.
* **Turnkey NASA SBIR/STTR Phase I Proposal ($225,000):** Fully formatted technical proposal, work breakdown structure, and milestone schedule aligned with subtopics TX07.01 (ISRU) and TX12.01 (In-Space Manufacturing).
* **Zero Dependencies:** Fully static, lightweight browser delivery powered by Tailwind CSS, Three.js, Chart.js, and KaTeX.

---
© 2026 RF WaveCode Incorporated. All rights reserved; the simulation software, algorithms, and digital twin models are proprietary and may not be reproduced, modified, or distributed without prior written permission.
## Mathematical Formulation

The densification auditor models complex impedance decay as a function of cumulative absorbed energy $E$ and nanophase iron content:

$$Z(E) = Z_{\text{final}} + \frac{Z_{\text{initial}} - Z_{\text{final}}}{1 + \exp\left[s \cdot (E - E_{\text{inflection}})\right]}$$

Where:

* $Z_{\text{initial}} \approx 1250 \ \Omega$ (Loose unconsolidated regolith powder)
* $Z_{\text{final}} \approx 85 \ \Omega$ (Dense sintered basalt ceramic)
* $s = 2.8$ (Sigmoidal consolidation steepness constant)
* $E_{\text{inflection}}$ scales dynamically with $\text{np-Fe}^0$ concentration ($0.10 \text{ wt}\%$ highland anorthosite to $1.50 \text{ wt}\%$ mare agglutinate)

If the measured deviation exceeds the safety threshold:

$$|Z_{\text{live}} - Z_{\text{target}}| > \Delta Z_{\text{threshold}}$$

The closed-loop daemon throttles the RF duty cycle to preserve structural yield metrics:

$$\sigma_{\text{compressive}} \ge 30.0 \text{ MPa}$$

---

## Tech Stack

| Layer | Technology | Purpose |
| :--- | :--- | :--- |
| **3D Cavity Renderer** | Three.js r128 | Resonant cavity, standing wave rings, workpiece heat map |
| **Telemetry Charting** | Chart.js | Dynamic $(E, Z)$ decay track and ideal trajectory overlay |
| **Interface and Styling** | Tailwind CSS | Lunar dark-mode telemetry dashboard |
| **Physics Engine** | Native ES6 JavaScript | Deterministic 100 ms discrete state engine |

---

## Quickstart and Local Setup

The repository is built entirely with client-side web technologies and requires no compilers, build pipelines, or package managers.

### 1. Clone the repository

```bash
git clone [https://github.com/msamsonov1/regolith-impedance-sintering-sim.git](https://github.com/msamsonov1/regolith-impedance-sintering-sim.git)
cd regolith-impedance-sintering-sim
