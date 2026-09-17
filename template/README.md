# 📋 PSU Model Template — How to Use

This folder contains a ready-to-copy template for adding a new PlayStation 1 PSU model page to the collection.

## What's inside

```
template/
├── README.md                    # this file
└── psu/
    └── MODELNAME/
        ├── README.md            # the actual per-model README template
        ├── photos/              # board photos → <SONY#>-top.png, <SONY#>-bottom.png
        └── schematics/          # schematic → <MODEL>.svg / <MODEL>.png
```

This mirrors the convention used by the real models, e.g. [`psu/ETXA87C2J/`](../psu/ETXA87C2J/).

## How to create a new model page

1. **Copy the folder:**
   ```bash
   cp -r template/psu/MODELNAME psu/<YOUR_MODEL>
   ```
2. **Fill in the placeholders** in `README.md`:
   - `<MODEL>` — man&mu;Facturer model number, e.g. `ZSSR697MA`
   - `<N>` — pin count, e.g. `7`, `5`
   - `<VOLTAGE>` — mains rating, e.g. `100–120V`, `220–240V`
   - `<MAN&mu;FACTURER>` — e.g. `Nichicon`, `Mitsumi`, `Matsushita (Panasonic)` etc.
   - `<Sony#>` — Sony part number, e.g. `1-468-219-13`
3. **Drop in your assets:**
   - board photos → `photos/` (top/bottom)
   - schematic → `schematics/`
   - datasheet PDFs → root [`datasheets/`](../datasheets/) (shared across models!).
4. **Add a row** to the model table in [`psu/README.md`](../psu/README.md).

> 💡 A PR doesn't need to be complete — photos alone, or a capacitor list alone, is perfectly fine.

## License

The template itself is [CERN-OHL-W v2](../LICENSE) — the same as the whole repository.
