# y⁺ Wall Calculator

A lightweight, browser-based CFD pre-processing tool for computing the first cell height (y⁺) and boundary layer mesh parameters. No installation, no dependencies — just open `index.html`.

**Live tool →** [yplus-calculator.vercel.app](https://yplus-calculator.vercel.app)  
**Portfolio →** [ivanpujol.vercel.app](https://ivanpujol.vercel.app)

---

## What it does

In CFD simulations, the accuracy of wall-bounded flow predictions depends heavily on how the first mesh cell is sized relative to the viscous sublayer. This tool automates those calculations given fluid properties, flow conditions, and a target y⁺ value.

---

## Features

- **Auto-detects flow regime** — Laminar, Turbulent, or Transitional from Reynolds number
- **Supports External & Internal flow** domains (flat plate / pipe)
- **Four empirical correlations** with validity ranges:
  - Blasius — Laminar, External (Re < 5×10⁵)
  - Schlichting — Turbulent, External (5×10⁵ < Re < 10⁷)
  - Hagen-Poiseuille — Laminar, Internal (Re < 2300)
  - Petukhov — Turbulent, Internal (3×10³ < Re < 5×10⁶)
- **y⁺ slider** with quick presets (y⁺ = 1 / 5 / 30 / 100)
- **Step-by-step formula breakdown** — Cf → τ_w → u_τ → y₁
- **Prism layer recommendation** — number of layers and total stack height based on growth ratio

## Outputs

| Output | Symbol | Unit |
|---|---|---|
| Reynolds Number | Re | — |
| Skin Friction Coefficient | Cf | — |
| Kinematic Viscosity | ν | m²/s |
| Wall Shear Stress | τ_w | Pa |
| Friction Velocity | u_τ | m/s |
| **First Cell Height** | **y₁** | **m** |
| Boundary Layer Thickness (external) | δ | m |
| Recommended Prism Layers | — | — |

---

## Usage

### Online
Visit the live deployment — no setup required.

### Local
```bash
git clone https://github.com/YOUR_USERNAME/yplus-calculator.git
cd yplus-calculator
open index.html   # or just double-click it
```

No build step, no npm, no dependencies. Pure HTML, CSS, and vanilla JavaScript.

---

## Inputs

| Parameter | Symbol | Unit |
|---|---|---|
| Fluid Density | ρ | kg/m³ |
| Dynamic Viscosity | μ | Pa·s |
| Free-stream / Bulk Velocity | U∞ | m/s |
| Reference Length / Hydraulic Diameter | L or D | m |
| Target y⁺ | y⁺ | — |
| Prism Layer Growth Ratio | GR | — |

**Default values** are set to air at standard sea-level conditions (ρ = 1.225 kg/m³, μ = 1.81×10⁻⁵ Pa·s).

---

## Empirical Correlations

### Blasius (Laminar, External)
$$C_f = \frac{1.328}{\sqrt{Re_L}}$$

Valid for laminar flat plate flow, Re_L < 5×10⁵.

### Schlichting (Turbulent, External)
$$C_f = \frac{0.370}{(\log_{10} Re_L)^{2.584}}$$

Valid for turbulent flat plate flow, 5×10⁵ < Re_L < 10⁷.

### Hagen-Poiseuille (Laminar, Internal)
$$f = \frac{64}{Re_D} \quad \Rightarrow \quad C_f = \frac{16}{Re_D}$$

Valid for fully developed laminar pipe flow, Re_D < 2300.

### Petukhov (Turbulent, Internal)
$$f = (0.790 \ln Re_D - 1.64)^{-2} \quad \Rightarrow \quad C_f = \frac{f}{4}$$

Valid for turbulent pipe flow, 3×10³ < Re_D < 5×10⁶.

### First Cell Height
All correlations feed into the same final chain:

$$\tau_w = C_f \cdot \tfrac{1}{2}\rho U^2 \qquad u_\tau = \sqrt{\frac{\tau_w}{\rho}} \qquad y_1 = \frac{y^+ \cdot \nu}{u_\tau}$$

---

## Tech Stack

- **HTML5 / CSS3 / Vanilla JavaScript** — zero dependencies
- **Fonts:** Inter, Lora, JetBrains Mono (Google Fonts)
- **Deployment:** Vercel

---

## Author

**Ivan Pujol** — Mechanical Engineer & CFD Specialist  
[ivanpujol.vercel.app](https://ivanpujol.vercel.app)

---

## License

MIT — free to use, modify, and distribute.
