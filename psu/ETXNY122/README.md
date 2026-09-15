# Matsushita (Panasonic) ETXNY122 (NPX122J1-1) PSU for Sony PlayStation (PSX/PS1) &ndash; reverse engineering

Late "fat" model power supply family.

| Sony # | Manufacturer # | Voltage | Models | Notes |
| :--- | :--- | :--- | :--- | :--- |
| `1-468-176-11` | `ETXNY122J1B` (NPX122J1-1) | 100V | SCPH-5500, 7000, 7500, 9000 | Japan |
| `1-468-218-11` | `ETXNY122A1B` | 120V | SCPH-5501, 7001, 7501, 9001 | North America |
| `1-468-219-21` | `ETXNY122E1B` (NPX122E1-1) | 220–240V | SCPH-5502, 7002, 7502, 9002 | Europe |
| `1-468-243-11` | `ETXNY122M1B` (NPX122M1-1A) | 100–240V | SCPH-550x, 700x, 750x, 900x | Asia (universal) |

## Schematics

### `ETXNY122J1B` (NPX122J1-1)

![ETXNY122J1B Schematic](schematics/1-468-176-11.png)

### `ETXNY122M1B` (NPX122M1-1A)

![ETXNY122M1B Schematic](schematics/1-468-243-11.svg)

## Photos

| Board top | Board bottom |
| :--- | :--- |
| ![Board top](photos/1-468-176-11-top_no_bg.png) | ![Board bottom](photos/1-468-176-11-bottom_no_bg.png) |

## Capacitors

For `1-468-219-21` (ETXNY122E1B). Source: [RetroSix Wiki — Capacitors (Sony PlayStation 1)](https://retrosix.wiki/wiki/capacitors-sony-playstation-1). All THT.

| Designator | Value | Voltage | Mounting |
| :--- | :--- | :--- | :--- |
| C107 | 1uF | 50V | THT |
| C003 | 47uF | 400V | THT |
| C104, C105 | 120uF | 25V | THT |
| C102, C103 | 560uF | 25V | THT |