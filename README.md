# PlayStation (PS1/PSX) Power Supplies — Reverse Engineering Collection

Collection of reverse-engineering documentation for the internal and developer power supply units used in the original Sony PlayStation (fat) and PlayStation debug/TOOL hardware.

> ⚠️ **Work in Progress.** Diagrams, BoMs and notes are personal reverse-engineering efforts. They may contain errors and are **not** verified for manufacturing. Working on line-powered PSUs is dangerous — respect mains safety.

## Model List

The full (work-in-progress) cross-reference of Sony part numbers, manufacturers, voltages and console models live in [PS1_PSU_models_list.md](PS1_PSU_models_list.md).

## PSU Documentation

Each PSU family lives in its own folder under [`psu/`](psu/). ✅ = resource present, blank = not yet.

| Manufacturer | Model family | Connector | Schematics | BOM | Photos |
| :--- | :--- | :--- | :---: | :---: | :---: |
| Matsushita (Panasonic) | [**ETXA87C2J**](psu/ETXA87C2J/) | 7-pin | ✅ | ✅ | ✅ |
| Matsushita (Panasonic) | [**ETXNY029**](psu/ETXNY029/) | 7-pin | | | ✅ |
| Matsushita (Panasonic) | [**ETXNY122**](psu/ETXNY122/) | 5-pin | | | ✅ |
| Matsushita (Panasonic) | [**ETXNY169**](psu/ETXNY169/) | 5-pin | | | ✅ |
| Matsushita (Panasonic) | [**ETXNY209**](psu/ETXNY209/) | 5-pin | | | ✅ |
| Mitsumi | [**SR670**](psu/SR670/) | 7-pin | | | |
| Mitsumi | [**SR674**](psu/SR674/) | 7-pin | | | |
| Mitsumi | [**SR678**](psu/SR678/) | 5-pin | | | ✅ |
| Mitsumi | [**SR679**](psu/SR679/) | 5-pin | | | ✅ |
| Fujitsu | [**KS350-1401-H039/05**](psu/KS350-1401-H039-05/) | 7-pin | | | |
| Nichicon | [**ZSSR654HA**](psu/ZSSR654HA/) | 7-pin | | | |
| Nichicon | [**ZSSR694MA**](psu/ZSSR694MA/) | 5-pin | | | |
| Nichicon | [**ZSSR697MA**](psu/ZSSR697MA/) | 5-pin | | | |
| Nichicon | [**ZSSR698HA**](psu/ZSSR698HA/) | 5-pin | | | ✅ |
| Nichicon | [**ZSSR706HA**](psu/ZSSR706HA/) | 5-pin | | | ✅ |
| Sony | [**PS-378**](psu/PS-378/) | dev (12V) | | | ✅ |

## Repository Layout

```
├── psu/                 ← per-model PSU documentation
│   ├── <MODEL>/
│   │   ├── README.md    ← model overview, specs, revisions
│   │   ├── schematics/  ← .svg/.png/.eprj2
│   │   ├── photos/      ← board top/bottom photos
│   │   └── revisions/   ← notes per revision (optional)
├── _originals/          ← original raw photos (before background removal)
├── datasheets/          ← (moved under psu/<MODEL>/datasheets/)
└── PS1_PSU_models_list.md
```

> Note: component datasheets for ETXA87C2J live in [`psu/ETXA87C2J/datasheets/`](psu/ETXA87C2J/datasheets/).

## 📄 License

This project is licensed under the **CERN Open Hardware Licence Version 2 - Weakly Reciprocal (CERN-OHL-W)**. See the `LICENSE` file for the full text.

**TL;DR:** You are free to use, modify, and distribute this hardware design. If you modify the source (the schematics), you must share your changes under the same license. Commercial use is allowed, provided that the source of the design remains open and you give appropriate credit.

## 🙏 Acknowledgments

I dedicate this work to everyone keeping the PlayStation alive and well.

---
**Disclaimer:** I am not affiliated with Sony or Panasonic. All trademarks are the property of their respective owners. This project is for educational and repair purposes only.