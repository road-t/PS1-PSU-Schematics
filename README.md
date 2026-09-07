# Sony PlayStation (PSX/PS1) 7-pin internal PSU &ndash; ETXA87C2J Reverse Engineering

[![Status: Work in Progress](https://img.shields.io/badge/Status-WIP-yellow)](https://github.com/yourusername/ps1-psu-etxa87c2j)
[![License: CERN-OHL-W v2](https://img.shields.io/badge/License-CERN--OHL--W%20v2-blue)](LICENSE)

## ⚠️ IMPORTANT DISCLAIMER & PROJECT STATUS

**This is a Work in Progress (WIP).**

This repository contains my personal reverse-engineering efforts for the **Sony PlayStation 1 7-pin internal Power Supply Unit model ETXA87C2J** (Panasonic/Matsushita manufactured, Japan 100V variant).

### 🚧 Project Status & Known Limitations
- **Schematic is incomplete and UNVERIFIED:** The provided schematic is a best-effort reconstruction based on tracing a physical board. It may contain errors, missing components, or incorrect net labels.
- **Testing is ongoing:** I have **not yet fully verified** that the schematic is 100% accurate under all load conditions.
- **Use at your own risk:** This is a **high-voltage device**. Incorrect assumptions can lead to dangerous short circuits, component damage, or personal injury. Do not use this schematic as a primary source for manufacturing or cloning without independent verification.

### 🤝 Contributions & Corrections
If you spot an error, have additional information, or have successfully repaired your own ETXA87C2J PSU, I strongly encourage you to open a **GitHub Issue** or submit a **Pull Request** with your findings. Your contribution can help others.

---

## 📚 Overview
This repository documents the internal circuitry of the **ETXA87C2J** — a 7-pin internal PSU manufactured by Matsushita (Panasonic) for the Sony PlayStation 1. This is a **Japan (100V)** variant, found in SCPH-1000, early SCPH-1001, SCPH-3000/SCPH-3500 through SCPH-5000 consoles.

The goal is to provide:
1.  A clear, readable schematic for diagnostics and repair.
2.  Technical notes on the design, based on physical board tracing.

### Known Revisions

This schematic covers the **NPXA87J** family:

| Sony Part No. | Panasonic Part No. | Tested |
| :--- | :--- | :--- |
| 1-413-997-12 | ETXA87C2J (NPXA87J-1B) | |
| 1-413-997-13 | ETXA87C2J (NPXA87J-1C) | |
| 1-413-997-14 | ETXA87C2J (NPXA87J-1D) | &#9989; |
| 1-413-997-15 | ETXA87C2J (NPXA87J-1E) | &#9989; |

See [psdevwiki](https://psdevwiki.com/ps1/Power_supplies) for the full 7-pin PSU list.

## 📂 Repository Structure
```
ETXA87C2J/
├── README.md
├── schematics/
│   ├── ETXA87C2J.png          # Schematic image (raster)
│   └── ETXA87C2J.svg          # Schematic image (vector)
└── project/
    └── SCH_PS1-PSU-7pin.eprj2 # EasyEDA source project
```

### Schematic

![ETXA87C2J Schematic](schematics/ETXA87C2J.png)

## 📷 Board Photos

Photos of the original board (high resolution, beware of file size).

### Top / Bottom

| Top side | Bottom side |
| :--- | :--- |
| ![Board top](img/top.png) | ![Board bottom](img/bottom.png) |

### Close-ups

| Component | Photo |
| :--- | :--- |
| **C003** (input filter cap) | ![C003](img/C003.png) |
| **IC101** (AN6562 op-amp) | ![IC101](img/IC101.png) |
| **PC001** (PS2501 optocoupler) | ![PC001](img/PC001.png) |
| **Q001** (2SC4953 switching transistor) | ![Q001](img/Q001.png) |

## 🔧 Component List & Common Substitutions

Values verified against the EasyEDA schematic (SVG). Full list is in the EasyEDA BOM / `/project/` export.

Note: in the EasyEDA BOM all zener diodes are placed on the **1N5348B** footprint (5W through-hole); the schematic value labels (below) are the electrical values.

Ceramic capacitor codes are the standard **EIA 3-digit pF code** printed on the body (e.g. `104` = 0.1&mu;F, `102` = 1nF). Primary-side caps (input/DC bus): **min 200V**. Secondary side (output rails ~3.5–8V): **min 16V**. If a primary cap is used as a snubber across Q001/Q002 switching node, use ≥1kV.

| Component | Original Label | Actual Chip / Function | Voltage | Recommended Substitute / Notes |
| :--- | :--- | :--- | :--- | :--- |
| **C001, C002** | 104K2B | 0.1&mu;F filter/decoupling capacitors (primary) | 250V | |
| **C003** | 150&mu;F 200V 105&deg;C | High-Voltage Filter Capacitor | 200V | Could be replaced with 150&mu;F, **400V** |
| **C004** | 102M | 1nF capacitors (primary) | 250V | |
| **C006** | BE 221K 1kV | 220pF capacitor (primary) | 1000V | ≥1kV if used as snubber |
| **C007** | 224C | 0.22&mu;F capacitor (primary) | 250V | |
| **C008** | 682JF | 6.8nF capacitor (primary) | 1000V | ≥1kV if used as snubber |
| **C009** | 104C | 0.1&mu;F filter capacitor (primary) | 250V | |
| **C010** | HR102 | 0.1&mu;F filter capacitor (primary) | 250V | |
| **C101, C102, C103** | 560&mu;F 25V | Output Filter Capacitors | 25V | Could be replaced with **680&mu;F 25-35V** (Low ESR) for a minor upgrade |
| **C104** | 180&mu;F 16V | Output Filter Capacitor | 25V | Could be replaced with **220&mu;F 25-35V** (Low ESR) |
| **C105, C106** | 104C | 0.1&mu;F decoupling capacitors (secondary) | 250V | |
| **C107** | 1uF 50V | 1&mu;F capacitor (secondary) | 25V | |
| **D001&ndash;D011** | 045x | Rectifier diodes | 200V | Unknown type |
| **D101/D102** | MA10799 | **MA10799** &ndash; Dual Schottky Diodes, Common Cathode | 200V | **STPS2045CT** (a reliable, higher-current replacement) |
| **F001** |250V 2A | Input fuse | 250V |
| **IC101** | 6562 | **AN6562 (AN1358)** &ndash; Dual Op-Amp Key feedback controller | 200V | **LM358N / LM358P** (a perfect, modern drop-in replacement) |
| **L001** | | Common-mode choke | 200V | ??? |
| **L101, L102** | | Output inductors | 200V | ??? |
| **PC001** | 2501 | Optocoupler (feedback isolation) | 200V | PS2501 |
| **PD101** | | Power LED (green, 5mm) | N/A |
| **Q001** | C4953 | **2SC4953** &ndash; NPN Transistor (body connected to the heatsink) | 400V | **ST13005** (verified compatible), but needs an insulator for heatsink to prevent collector-emitter short circuit |
| **Q002** | D1302 | High-voltage switching transistor | 2SD1302 |
| **Q101, Q102** | N4211  | Digital bias transistors | UN4211 |
| **Q103** | N4210 | Digital bias transistor | UN4210 |
| **R001** | brown-black-green-gold | 1M&Omega; resistor | 1/4W |
| **R002** | brown-green-yellow-gold | 150k&Omega; resistor | 1/8W |
| **R003** | red-violet-red-gold | 2.7k&Omega; resistor | 1/8W |
| **R004** | yellow-violet-black-gold | 47&Omega; resistor | 1W |
| **R005** | brown-black-yellow-gold | 100k&Omega; resistor | 1/4W |
| **R006, R109** | brown-black-brown-gold | 100&Omega; resistors | 1/2W |
| **R007, R010** | red-red-brown-gold | 220&Omega; resistors | 1/8W |
| **R008, R009** | orange-white-brown-gold | 390&Omega; resistors | 1/8W |
| **R101** | orange-orange-brown-gold | 330&Omega; resistor | 1/8W |
| **R102** | brown-orange-brown-gold | 130&Omega; resistor | 1/8W |
| **R103, R105** | green-blue-brown-gold | 560&Omega; resistors | 1/8W |
| **R104** | red-red-red-gold | 2.2k&Omega; resistor | 1/8W |
| **R106** | orange-black-red-gold | 3k&Omega; resistor | 1/8W |
| **R107** | red-yellow-red-gold | 2.4k&Omega; resistor | 1/8W |
| **R108** | orange-orange-red-brown-brown | 3.32k&Omega; resistor | 1/8W |
| **R110** | blue-grey-red-gold | 6.8k&Omega; resistor | 1/8W |
| **R111** | orange-orange-black-gold | 33&Omega; resistor | 1/8W |
| **R113** | green-blue-red-gold | 5.6k&Omega; resistor | 1/8W |
| **R114** | blue-grey-black-gold | 68&Omega; resistor | 1/4W |
| **T001** | BD131A | Switching transformer | ??? |
| **VR101** | | Variable resistor (pot) | 110&ndash;120&Omega; &mdash; verify function on PCB |
| **ZD001** | Yellow-brown-brown | 4.3V Zener Diode | 1/2W |
| **ZD002** | Yellow-violet-violet | 4.7V Zener Diode | 1/2W |
| **ZD101** | Brown-red | 12V Zener Diode (1W) | 1W |
| **ZD102, ZD103** | Green-brown-brown | 5.1V Zener Diode | 1/2W |

## 🛠️ How to Use This Information
1.  **Download the schematic:** Use it as a reference while troubleshooting your PSU.
2.  **Diagnose common faults:** Use the table above to identify and replace known failure points (e.g., capacitors, the IC101 op-amp, switching transistor Q001).
3.  **Understand the design:** Follow the circuit to learn how the PSU generates stable 7.6V and 3.3V outputs.
4.  **Discharge C003 before touching:** After unplugging from the mains, **discharge the input capacitor C003** with a discharge tool (screwdriver with insulated handle will do), or wait at least **5 minutes** for it to drain through the bleed resistors. The charge stays on the pins for a long time — do not skip this, it hurts.
5.  **Proceed with caution:** This is a line-powered switching power supply. Dangerous voltages are present inside. Work only if you have the necessary experience and safety equipment.

## 🧪 Testing & Verification Process
If the fuse **F001 blows** (e.g., during commissioning after repair), use an **incandescent bulb in series** with the PSU before plugging into the mains. The bulb limits current and protects the PSU from damage:

- **Bulb stays dark** = PSU is fine, no short circuit.
- **Bulb lights up and stays on** = something is shorted (bad rectifier diode, blown switching transistor, shorted filter cap). Find it before powering on.
- **Bulb briefly flashes then goes out** = normal inrush into C003, PSU is starting up as expected.
- Use a bulb with a power rating roughly matching the PSU's load (e.g., 40–100W for a ~50W PSU) so it doesn't drop too much voltage while testing.

## 📄 License

This project is licensed under the **CERN Open Hardware Licence Version 2 - Weakly Reciprocal (CERN-OHL-W)**. See the `LICENSE` file for the full text.

**TL;DR:** You are free to use, modify, and distribute this hardware design. If you modify the source (the schematics), you must share your changes under the same license. Commercial use is allowed, provided that the source of the design remains open and you give appropriate credit.

## 🙏 Acknowledgments
I dedicate this work to everyone keeping the PlayStation alive and well.

---
**Disclaimer:** I am not affiliated with Sony or Panasonic. All trademarks are the property of their respective owners. This project is for educational and repair purposes only.