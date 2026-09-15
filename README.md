# PlayStation (PS1/PSX) Power Supplies — Reverse Engineering Collection

Collection of reverse-engineering documentation for the internal and developer power supply units used in the original Sony PlayStation (fat).

[![Status: Work in Progress](https://img.shields.io/badge/Status-WIP-yellow)](https://github.com/road-t/PS1-PSU-Schematics)
[![License: CERN-OHL-W v2](https://img.shields.io/badge/License-CERN--OHL--W%20v2-blue)](../../LICENSE)

⚠️ **Work in Progress.** Diagrams, BoMs and notes are personal reverse-engineering and researching efforts. They may contain errors and could be used at your own risk. Remember, that **working on line-powered PSUs is dangerous** — respect mains safety.

### 🤝 Contributions & Corrections

This project needs a **community effort**. There are dozen of different PS1 power supplies out there, and most of them still have **empty boxes** in the [model list](psu/README.md) — no schematics, no BOM, no photos. Every single model deserves a full page.

If you own a PSU that isn't documented yet, **please help**. Contributions in any form are welcome:

- **Corrections** — spot a wrong value, pinout, trace or a model↔manufacturer number mismatch? Open an issue or fix it directly and create a pull request.
- **New data** — missing PSU model, board photos, component data, or a full reverse-engineering page for a PSU in your hands.
- **Verification** — you actually installed a replacement part? Report how it went.

> 🙏 **Help is badly needed.** Any contribution, however small, is **invaluable for the retro-gaming community** — a documented PSU makes repairing a PS1 approachable for anyone with a soldering ironchers. A single photo or a component list from a model that currently has nothing is already a huge win.

#### Suggested Pull-request format

To keep the repo consistent, please use this structure when adding or updating a PSU:

```
psu/<MODEL>/
├── README.md          # model table + capacitor table (required)
├── schematics/        # schematic images (PNG/SVG)
├── photos/            # high-res board photos: <MODEL>-top.png, <MODEL>-bottom.png
└── bom/               # optional: full BoM in CSV/Markdown
```

Datasheets are **shared** — one folder at the repo root, `datasheets/`. Do **not** duplicate them under each `psu/<MODEL>/`; components (e.g. `2SC4953`, `PS2501`, `AN1358`) are reused across many PSUs, so a single copy is enough.

**Conventions**

| Rule | Example |
| :--- | :--- |
| Folder name = manufacturer model # in uppercase, no Sony "#", no spaces | `psu/ETXA87C2J`, `psu/ZSSR797MA` |
| README starts with a single `# <MODEL> (<Manufacturer>)` line | `# ETXA87C2J (Matsushita/Panasonic)` |
| Model table columns: `Sony # | Manufacturer # | Voltage | Models | Motherboards | Notes` | see [ETXA87C2J](psu/ETXA87C2J/README.md) |
| Capacitors go in their own `## Capacitors` section | Value / Voltage / Mounting |
| Use Unicode units | `&Omega;`, `&mu;F`, `THT`/`SMD` |
| Multi-model PSUs: use the Sony # in the folder body | `1-468-307-12` |
| Photos: `<MODEL>-<part>.png` | `ETXA87C2J-C003.png` |

A PR does **not** need to be complete: photos alone, or a components list alone, is perfectly fine. Just use the current repo style. Thank you in advance! 💚

## 📚 Overview
The goal is to provide schematics and components data for diagnostics and repair of PlayStation 1 PSUs.

## PSU Documentation

Each PSU family lives in its own folder under [`psu/`](psu/). ✅ = resource present, blank = not yet.

| Manufacturer | Model family | Connector | Schematics | BOM | Photos |
| :--- | :--- | :--- | :---: | :---: | :---: |
| Matsushita (Panasonic) | [**ETXA87C2J**](psu/ETXA87C2J/) | 7-pin | ✅ | ✅ | ✅ |
| Matsushita (Panasonic) | [**ETXNY029**](psu/ETXNY029/) | 7-pin | | | ✅ |
| Matsushita (Panasonic) | [**ETXNY122**](psu/ETXNY122/) | 5-pin |  ✅ | | ✅ |
| Matsushita (Panasonic) | [**ETXNY169**](psu/ETXNY169/) | 5-pin | | | ✅ |
| Matsushita (Panasonic) | [**ETXNY209**](psu/ETXNY209/) | 5-pin |  ✅ | | ✅ |
| Mitsumi | [**SR670**](psu/SR670/) | 7-pin | | | |
| Mitsumi | [**SR674**](psu/SR674/) | 7-pin | | | |
| Mitsumi | [**SR678**](psu/SR678/) | 5-pin | | | ✅ |
| Mitsumi | [**SR679**](psu/SR679/) | 5-pin | ✅ | | ✅ |
| Fujitsu | [**KS350-1401-H039/05**](psu/KS350-1401-H039-05/) | 7-pin | | | |
| Nichicon | [**ZSSR654HA**](psu/ZSSR654HA/) | 7-pin | | | ✅ |
| Nichicon | [**ZSSR694MA**](psu/ZSSR694MA/) | 5-pin | | | |
| Nichicon | [**ZSSR797MA**](psu/ZSSR797MA/) | 5-pin | | | ✅ |
| Nichicon | [**ZSSR698HA**](psu/ZSSR698HA/) | 5-pin | ✅ | | ✅ |
| Nichicon | [**ZSSR706HA**](psu/ZSSR706HA/) | 5-pin | ✅ | | ✅ |
| Sony | [**PS-378**](psu/PS-378/) | dev (12V) | | | ✅ |

## 🛠️ How to Use This Information
0. **Determine which model of PSU you have**. Use the [PS1 power supplies list](psu/README.md).
1.  **Download the schematic:** Use it as a reference while troubleshooting your PSU.
2.  **Diagnose common faults:** Use the table above to identify and replace known failure points (e.g., capacitors, the IC101 op-amp, switching transistor Q001).
3.  **Understand the design:** Follow the circuit to learn how the PSU generates stable 7.6V and 3.3V outputs.
4.  **Discharge C003 before touching:** After unplugging from the mains, **discharge the input capacitor C003** with a discharge tool (screwdriver with insulated handle will do), or wait at least **5 minutes** for it to drain through the bleed resistors. The charge stays on the pins for a long time — do not skip this, it hurts.
5.  ⚠️ **Proceed with caution:** This is a line-powered switching power supply. Dangerous voltages are present inside. Work only if you have the necessary experience and safety equipment.

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
**Disclaimer:** I am not affiliated with Sony, Matsushita (Panasonic), Mitsumi, Nichicon, Fujitsu and/or other manufacturers.
All trademarks are the property of their respective owners.
This project is for educational and repair purposes only.