# Matsushita (Panasonic) ETXNY209 (NPX209J1-1) PSU for Sony PlayStation (PSX/PS1) &ndash; reverse engineering

Late "fat" model power supply family.

| Sony # | Manufacturer # | Voltage | Models | Notes |
| :--- | :--- | :--- | :--- | :--- |
| `1-468-366-11` | `ETXNY209J1B` (NPX209J1-1) | 100-120V | SCPH-5500, 7000, 7500, 9000 | Japan |
| `1-468-365-11` | `ETXNY209A1B` | 100-120V | SCPH-5501, 7001, 7501, 9001 | North America |
| `1-468-365-12` | `ETXNY209A1BA` | 100-120V | SCPH-5501, 7001, 7501, 9001 | North America |
| `1-468-304-11` | `ETXNY209E1B` (NPX209E1-1) | 220–240V | SCPH-5502, 7002, 7502, 9002 | Europe |


## Schematics

*⚠️ The **ETXNY209A1B** (1-468-365-1x) and **ETXNY209J1B** (1-468-366-1x) are totally equal, besides the absence of the R005 resistor in
 **ETXNY209J1B**. However, the **ETXNY209J1B** schematic is [available](../schematics/1-468-366-11) as well.*

![ETXA87C2J Schematic](schematics/1-468-365-11.svg)

## Photos

| Board top | Board bottom |
| :--- | :--- |
| ![Board top](photos/1-468-304-11-top_no_bg.png) | ![Board bottom](photos/1-468-304-11-bottom_no_bg.png) |
| ![Board top](photos/1-468-366-11-top_no_bg.png) | ![Board bottom](photos/1-468-366-11-bottom_no_bg.png) |

## Capacitors

| Designator | Value | Voltage | Mounting |
| :--- | :--- | :--- | :--- |
| C003 | 120uF | 200V | THT |
| C104, C105 | 220uF | 25V | THT |
| C102, C103 | 560uF | 25V | THT |
