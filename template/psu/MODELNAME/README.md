# <MANUFACTURER> <OEM-PART#> PSU for Sony PlayStation (PSX/PS1) &ndash; specs, schematics and photos

### Known Revisions

| Sony Part No. | Manufacturer Part No. | Voltage | Models | Notes | Tested |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `1-xxx-xxx-xx` | `<MODEL>` (NPX<MODEL>-x) | 100&ndash;240V | SCPH-7003, 7503, 9003 | `<REGION>` |

See [my document](../psu/README.md) for the full (not sure)  PlayStation PSU list.

### Schematic

![<MODEL> Schematic](schematics/<MODEL>.svg)

## 📷 Board Photos

### Top / Bottom

| Top side | Bottom side |
| :--- | :--- |
| ![Board top](photos/<MODEL>-top.png) | ![Board bottom](photos/<MODEL>-bottom.png) |

## 🔧 Component List & Common Substitutions

*Replace with components for the current PSU*

| Component | Original&nbsp;Label | Actual Chip / Function | Voltage | Note |
| :--- | :--- | :--- | :--- | :--- |
| **C001, C002** | 104K2B | 0.1&mu;F filter/decoupling capacitors (primary) | 250V | |
| **C003** | 150&mu;F 200V 105&deg;C | High-Voltage Filter Capacitor | 200V | Main capacitor, blows up when gets 230V |
| **D001&ndash;D011** | 045x | Rectifier diodes | 200V | Unknown type |
| **D101/D102** | MA10799 | **[MA10799](../../datasheets/MA10799.PDF)** &ndash; Dual Schottky Diodes, Common Cathode | 200V |Could be replaced with **STPS2045CT** |
| **F001** |250V 2A | Input fuse | 250V |
| **IC101** | 6562 | **[AN6562 (AN1358)](../../datasheets/AN1358.PDF)** &ndash; Dual Op-Amp Key feedback controller | 200V | Could be replaced with **LM358N / LM358P** |
| **L001** | N/A | Common-mode choke | 200V | 100mH |
| **PC001** | 2501 | **[PS2501](../../datasheets/PS2501.PDF)** &ndash; Optocoupler (feedback isolation) | 200V | PS2501 |
| **PD101** | N/A | Power LED (green, 5mm) | N/A |
| **Q001** | C4953 | **[2SC4953](../../datasheets/2SC4953.PDF)** &ndash; NPN Transistor | 400V | Could be replaced with **ST13005** (verified compatible), but needs an insulator for heatsink to prevent collector-emitter short circuit |
| **R001** | 🟫 ⬛ 🟩 🟡 | 1M&Omega; resistor | N/A | 1/4W, 5% |
| **R009** | 🟡 🟥 🟥 🟫 🟤 | 4.22k&Omega; resistors | N/A | 1/8W, 1%|
| **T001** | BD131A | Switching transformer | N/A | ??? | |
| **VR101** | N/A | Variable resistor (pot) | N/A | N/A | Usually reads in range 110&ndash;125&Omega; |
| **ZD001** | 🟨🟨 🟧 🟧 | 4.3V Zener Diode | 20V | 1/2W |
| **ZD101** | 🟫🟫 🟥 | 12V Zener Diode (1W) | 20V |1W |